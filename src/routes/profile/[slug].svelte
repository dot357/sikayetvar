<script context="module">
  import Footer from "./../../components/Footer.svelte";
  import Head from "./../../components/Head.svelte";

  export async function preload({ params, query }) {
    //console.log(params);
    const res = await this.fetch(
      `https://jsonplaceholder.typicode.com/users/${params.slug}`
    );
    const data = await res.json();

    return { userInfo: data };
  }
</script>

<script>
  export let userInfo;
  //console.log(userInfo);
</script>

<svelte:head>
  <title>{userInfo.name}</title>
</svelte:head>

<Head />

<div class="profileStyle">
  <div class="profileHeader">
    <div class="name"><h1>{userInfo.name}</h1></div>
    <div class="city"><h2>{userInfo.address.city}</h2></div>
  </div>

  <div class="profileBody">
    <div class="info">
      <p>
        <strong>Username </strong>
        {userInfo.username}
      </p>
      <p>
        <strong>Email </strong>
        <a href="mailto:{userInfo.email}">{userInfo.email}</a>
      </p>
      <p>
        <strong>Phone </strong>
        {userInfo.phone}
      </p>
      <p>
        <strong>Website </strong>
        <a href="http://{userInfo.website}" target="_blank"
          >{userInfo.website}</a
        >
      </p>
      <p>
        <strong>Company </strong>
        {userInfo.company.name}
      </p>

     
    </div>

    <div class="map">
      <iframe
        title={userInfo.name}
        width="425"
        height="350"
        frameborder="0"
        scrolling="no"
        marginheight="0"
        marginwidth="0"
        src="https://www.openstreetmap.org/export/embed.html?bbox={userInfo
          .address.geo.lng}%2C{userInfo.address.geo.lat}%2C{userInfo.address.geo
          .lng}%2C{userInfo.address.geo
          .lat}&amp;layer=mapnik&amp;marker={userInfo.address.geo
          .lat}%2C{userInfo.address.geo.lng}"
        style="border: 1px solid black"
      /><br /><small
        ><a
          href="https://www.openstreetmap.org/?mlat=-37.31590&amp;mlon=81.14826#map=17/-37.31590/81.14826"
          >Daha Büyük Haritayı Göster</a
        ></small
      >


      <p>
       <strong>Lat:</strong> {userInfo.address.geo.lat} , <strong>Lng:</strong> {userInfo.address.geo.lng}
      </p>
    </div>



  </div>
</div>

<Footer
  facebook="https://www.facebook.com/sikayetvar/"
  github="https://github.com/dot357"
  dribbble="#"
  twitter="#"
/>

<style>
  .profileStyle {
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

  .profileStyle .profileHeader {
    width: 100%;
    padding-top: 30px;
  }

  .profileStyle .profileHeader .name h1{
      
      color: #32325D;
      font-size: 28px;
      font-weight:normal;
     
  }

  .profileStyle .profileHeader .city h2{
    
      color: #32325D;
      font-size: 16px;
      font-weight:300;


  }

  .profileStyle .profileBody {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 1fr;
    grid-column-gap: 25px;
    grid-row-gap: 0px;
  }




  .profileStyle a {
      
      text-decoration: none;
   
   
    padding: 0.3em;
    padding-left: 0;
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

  .profileStyle a:hover,
  .profileStyle a:focus {
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



  .profileStyle .profileBody .info strong{
    
      display: inline-block;
      color:#ADB5BD;
      font-size: 14px;
      letter-spacing: 0.1px;
      width:90px;
      font-weight: 400;
  }


  .profileStyle .profileBody {
    

    color:#525F7F;
    font-size: 16px;
    font-weight: 600;
    
}

.profileStyle .profileBody .map{
    position:relative;
    top:-70px;
}

.profileStyle .profileBody .map p{
    font-size:14px;
}

.profileStyle .profileBody .map p strong{

      color:#ADB5BD;
      font-size: 12px;
      letter-spacing: 0.1px;
      
      font-weight: 400;
}

iframe{
   
    width:100%;
}


@media screen and (max-width: 920px) {
    .profileStyle .profileBody {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    grid-template-rows: 1fr;
    grid-column-gap: 25px;
    grid-row-gap: 0px;
  }
  .profileStyle .profileBody .map{
   
   top:10px;
}

    
}

@media screen and (max-width: 500px){

    .profileStyle .profileBody .info strong{
    
  
    width:70px;
    
}

}





</style>
