<script>
  import CloseModal from "./CloseModal.svelte";
  //for updating and deleting post I need some data. This data will be populated from Posts.svelte as props
  export let isOpen;
  //this is for checking is it called for update or delete process
  export let isUpdate;
  export let postId;
  export let userId;
  export let title;
  export let body;

  let modalStatus;
  let responseSave = [];

  //delete func
  async function deletePost() {
    modalStatus = "DELETED";
    await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`, {
      method: "DELETE",
    })
      .then((result) => {
        console.log(result);
        responseSave = result;
      })
      .catch((error) => {
        console.log(error);
      });
  }

  //update func
  function updatePost() {
    modalStatus = "UPDATED";
    fetch("https://jsonplaceholder.typicode.com/posts/1", {
      method: "PUT",
      body: JSON.stringify({
        id: postId,
        title: document.querySelector("#title").value,
        body: document.querySelector("#body").value,
        userId: userId,
      }),
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        console.log(json);
        responseSave = json;
      });
  }

  //closeModal
</script>

<div class="modalBox">
  <CloseModal bind:isOpen />

  {#if isUpdate}
    <h2>Düzenle</h2>
    <hr />

    <div class="form">
      <label>Title</label>
      <input id="title" type="text" value={title} />

      <label>Body</label>
      
      <textarea id="body" rows="6"  cols="50">{body} </textarea>
  
     
      <hr style="margin-top: 26px;">
      <button class="button" on:click={updatePost}>Güncelle</button>
    </div>
  {/if}

  {#if !isUpdate}
   <div class="isDelete">
    <h2>Silme işlemi</h2>
    <hr />

   <p>
    <strong>{title}</strong>  gönderiyi silmek istediğinizden emin misiniz?
    
   </p>

   <button on:click={deletePost}>SİL</button>
   </div>
  {/if}

    {#if modalStatus == "UPDATED"}
    <p class="updated">
      {modalStatus} INFO : <br />
      [ <strong>postId</strong> : {responseSave.id}, <strong>userId</strong> : {responseSave.userId},
      <strong>title</strong>
      : {responseSave.title}, <strong>body</strong> : {responseSave.body} ]
    </p>
    
    {/if}

    {#if modalStatus == "DELETED"}
    <p class="deleted">
      {modalStatus} RESPONSE : <br />
      [ {responseSave.status} , {responseSave.url}, {responseSave.type} ]
    </p>
    
    {/if}

  <p style="font-size: 0.8em;">
    INFO : <br />
    [ <strong>postId</strong> : {postId}, <strong>userId</strong> : {userId},
    <strong>title</strong>
    : {title}, <strong>title</strong> : {body} ]
  </p>
</div>
<div class="overlay" />

<style>
  .overlay {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.473);
    position: fixed;
    top: 0;
    left: 0;
    z-index:3;
  }

  .modalBox {
    z-index: 1999;
    background-color: white;
    border-radius: 4px;
    margin: auto auto;
    width: min(50%, 90%);
    color:  #32325D;
    box-shadow: 0px 15px 35px rgba(50, 50, 93, 0.1),
      0px 5px 15px rgba(0, 0, 0, 0.07);
    padding: 1.8em;
    top: 60px;
    position: fixed;
    left: 0;
    right: 0;
    margin-left: auto;
    margin-right: auto;
  }

 

  .form input {
    width: 98%;
    padding: 0.6em;
    margin: 0 auto;
    border-radius: 4px;
    margin-top: 10px;
    margin-bottom: 15px;
    border: 1px solid #CAD1D7;
    border-radius: 4px;
    padding: 12px;
    color: #8898AA;
    
  }
  .form input:focus{
    outline: none;
    border: 3px solid #CAD1D7;
    color: #5c6064;
  }

  .form textarea{
    resize: none;
    width: 98%;
    padding: 0.6em;
    margin: 0 auto;
    border-radius: 4px;
    margin-top: 10px;
    margin-bottom: 15px;
    border: 1px solid #CAD1D7;
    border-radius: 4px;
    padding: 12px;
    color: #8898AA;
    overflow: hidden;
  }

  .form textarea:focus{
    outline: none;
    border: 3px solid #CAD1D7;
    color: #5c6064;
  }

  label{
    font-weight: 600;

  }

  hr{
    width: 100%;
    border: none;
    border-bottom: 2px solid #E9ECEF;
    margin: 0 auto;
    margin-bottom: 26px;
  }


.button{
  background: #11CDEF;
  color: white;
  font-family: "Open Sans", sans-serif;
    outline: none;
    border: none;
    padding: 1em;
    text-transform: uppercase;
    box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.08),
      0px 4px 4px rgba(50, 50, 93, 0.11);
    border-radius: 3px;
    font-size: var(--fontSize-regular);
   
    letter-spacing: 0.8px;
    font-weight: 400;
    cursor: pointer;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    transition: all 0.25s ease;
}

.isDelete p{
  width: 100%;
}

.isDelete button{
  background: #FB6340;
  color: white;
  font-family: "Open Sans", sans-serif;
    outline: none;
    border: none;
    padding: 1em;
    text-transform: uppercase;
    box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.08),
      0px 4px 4px rgba(50, 50, 93, 0.11);
    border-radius: 3px;
    font-size: var(--fontSize-regular);
   
    letter-spacing: 0.8px;
    font-weight: 400;
    cursor: pointer;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    transition: all 0.25s ease;
}


.updated{
  font-size: 0.8em;
  color: #00cdac;
}

.deleted{
  font-size: 0.8em;
  color: #FB6340;
}

@media screen and (max-width: 920px) {
  .modalBox {
   
    width: 80%;
    top: 60px;
  }
  .form input,.form textarea{
   width:95.5%;
 }


}

@media screen and (max-width: 500px){
  .modalBox {
   
   width: 80%;
   top:25px;
 }
 .form input,.form textarea{
   width:91%;
 }
 


}

</style>
