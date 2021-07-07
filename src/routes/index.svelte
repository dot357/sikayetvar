
<svelte:head>
	<title>sikayetvar.com Test uygulaması  </title>

	<meta name="description" content="Bu uygulama Sapper & Svelte alt yapısı kullanarak yapılmıştır." />
	<meta name="author" content="Emre Can Eskimez">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
</svelte:head>

<script>
	import Posts from '../components/Posts.svelte'
	import Head from '../components/Head.svelte'
	import Footer from '../components/Footer.svelte'
</script>

<style>
	
</style>


<Head />
<Posts />
<Footer  facebook='https://www.facebook.com/sikayetvar/' github='https://github.com/dot357' dribbble='#' twitter='#'/>