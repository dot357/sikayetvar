<script>
  // This is a life cycle method just like window.onLoad
  import { onMount } from "svelte";
  import Modal from "./Modal.svelte";
  import CloseModal from "./CloseModal.svelte";

  let posts = [];
  //Post per page count
  let postPerPage = 6;
  let postPerPageStart = 0;
  let pageNumber = 0;
  let isOpen = false;
  let isUpdate = true;

  let modalProps = [];

  onMount(async () => {
    const res = await fetch("http://jsonplaceholder.typicode.com/posts");
    const json = await res.json();
    posts = json;
    //console.log(posts);
  });

  

  function nextPage() {
    //#debug
    /*console.log(`postPerPageStart : ${postPerPageStart}`);
    console.log(`postPerPage : ${postPerPage}`); */
    //swaping page numbers and increasing for next loop

    postPerPageStart = postPerPage;
    postPerPage = postPerPage + 6;
    pageNumber++;
  }

  function prevPage() {
    //#debug
    /*console.log(`postPerPageStart : ${postPerPageStart}`);
    console.log(`postPerPage : ${postPerPage}`);*/
    /* difrence between two numbers needs to be 6 in order to achive 6 posts per page */

    postPerPageStart = postPerPage - 12;
    postPerPage = postPerPage - 6;
    pageNumber--;
  }

  function openModal() {
    isOpen = true;
  }

  //fill object and push it into Modal with state true = update false = delete
  function propFiller(post,updateState) {
    isUpdate = updateState;
    modalProps = post;
   //console.log(post);
  }


</script>

{#if isOpen}
  <Modal
    bind:isOpen
    isUpdate={isUpdate}
    userId={modalProps.userId}
    body={modalProps.body}
    title={modalProps.title}
    postId={modalProps.id}
  />
{/if}

<ul class="posts textDarkBlue">
  {#each posts.slice(postPerPageStart, postPerPage) as post, i (post.id)}
    <li id="post{post.id}">
      <div>
        <div class="titles fLight">
          <span class="fBold textPaleBlue postCount">{post.id}</span> {post.title}
        </div>
        <div class="buttons">
          <a rel="prefetch" href="/post/{post.id}">
            <button class="bgBlue fBold textWhite btnDetay">detay</button></a
          >
          <button on:click={openModal} on:click={propFiller(post,true)} class="bgGreen fBold textWhite btnDuzen"
            >düzenle</button
          >
          <button on:click={openModal} on:click={propFiller(post,false)} class="bgRed fBold textWhite btnSil">SİL</button>
        </div>
      </div>
      <hr />
    </li>
  {/each}

  <div>
    <div class="pages">
      {#if postPerPageStart != 0}
        <a on:click={prevPage}>Önceki sayfa</a>
      {/if}
      {#if postPerPage <= 100}
        <a on:click={nextPage}>Sonraki sayfa</a>
      {/if}
    </div>
    <div class="pageNumbers">
      <strong>Sayfa numarası :</strong>
      {pageNumber + 1}
    </div>
  </div>
</ul>

<style>
  /* general styling for default elements */
  :root {
    --colorBlue: #5e72e4;
    --colorDarkBlue: #32325d;
    --colorPaleBlue: #525f7f;
    --colorGreen: #2dce89;
    --colorRed: #fb6340;

    --bgBlue: #5e72e4;
    --bgGreen: #2dce89;
    --bgRed: #fb6340;

    --fontLight: 300;
    --fontRegular: 400;
    --fontBold: 700;

    --fontSize-regular: 14px;
  }

  /* font weights*/
  .fLight {
    font-weight: var(--fontLight);
  }

  .fRegular {
    font-weight: var(--fontRegular);
  }

  .fBold {
    font-weight: var(--fontBold);
  }

  /* background colors*/

  .bgBlue {
    background-color: #5e72e4;
  }

  .bgGreen {
    background-color: #2dce89;
  }
  .bgRed {
    background-color: #fb6340;
  }

  /*text colors*/

  .textWhite {
    color: white;
  }

  .textDarkBlue {
    color: var(--colorDarkBlue);
  }
  .textPaleBlue {
    color: var(--colorPaleBlue);
  }

  /* Define buttons */
  .buttons button {
    font-family: "Open Sans", sans-serif;
    outline: none;
    border: none;
    padding: 1em;
    text-transform: uppercase;
    box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.08),
      0px 4px 4px rgba(50, 50, 93, 0.11);
    border-radius: 3px;
    font-size: var(--fontSize-regular);
    margin-left: 7px;
    margin-right: 7px;
    letter-spacing: 0.8px;
    cursor: pointer;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    transition: all 0.25s ease;
  }

  .buttons button:hover,
  .buttons button:focus {
    /* I include focus because while i am developing i care about accessibility for disabled people */
    transform: translateY(-0.25rem);
    box-shadow: 0px 0px 7px -3px #010730af;
  }

  

  ul {
    margin: 0 auto;
    margin-top: 5em;
    padding-left: 2em;
    padding-right: 2.1em;
    padding-top: 1em;
    padding-bottom: 1em;
    min-height: 500px;
    font-family: "Open Sans", sans-serif;
    list-style: none;
    background-color: white;
    width: min(75%, 90%);
    box-shadow: 0px 15px 35px rgba(50, 50, 93, 0.1),
      0px 5px 15px rgba(0, 0, 0, 0.07);
    border-radius: 4px;
  }
  .posts li {
    width: 100%;
  }
  .posts li div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-top: 11px;
  }
  .posts .titles span{
    margin-right:10px;
  }

  

  .postCount {
    margin-left: 10px;
  }

  .buttons {
    display: flex;
    flex-direction: row;
    justify-content: center;
  }

  hr {
    width: 100%;
    border: none;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
     padding-top:11px;
     margin-bottom:11px;
  }

  .pages {
    display: flex;
    flex-direction: row;
    justify-content: center;
  }

  .pages a {
    margin: 8px 8px;
    padding: 0.3em;
    cursor: pointer;
    background: linear-gradient(to bottom, #8ddad5 0%, #00cdac 100%);
    background-position: 0 100%;
    background-repeat: repeat-x;
    background-size: 1px 1px;
    /* for disabling sellection on page indicators*/
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    transition: all 0.15s ease-in;
  }

  .pages a:hover,
  .pages a:focus {
    color: white;
    font-weight: bold;
    letter-spacing: 1px;
    text-decoration: none;
    position: relative;
    font-weight: 400;
    background: linear-gradient(to bottom, #8ddad5 0%, #00cdac 100%);
    background-position: 0 100%;
    background-repeat: repeat-x;
    background-size: 35px 35px;
    box-shadow: 0px 0px 13px -8px rgba(0, 0, 0, 0.288);
  }

  .pageNumbers {
    padding-top: 5px;
    text-align: center;
  }

  @media screen and (max-width: 920px) {

    .posts li div {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    margin-top: 11px;
  }

  .buttons{
    width:100%;
  }

  .buttons button{
    width:100%;
    margin-bottom: 7px;
  }

  .buttons a  {
    width:100%;
  
  }
  .posts .titles{
    padding-left: 7px;
  }
  .posts .titles span{
    margin:0;
  }


  }
</style>
