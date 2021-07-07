<script>
	export let segment;
</script>

<style>
	nav {
		background: transparent;
		width: 100%;
		color:white;
		font-weight: 300;
		
		
	}

	ul {
		margin: 0 auto;
		width: min(77%, 90%);
		background: transparent;
		display: flex;
		justify-content: start;
		align-items: baseline;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		font-family: 'Open Sans', sans-serif;
		display: block;
		float: left;
		transition: all 0.15s ease-in;
	}
	li:hover{
		transform: translateY(-0.25rem);

	}

	nav ul .loginButton {
		margin-left: auto;
	}
	nav ul .loginButton a{
	font-family: "Open Sans", sans-serif;
	color:#5E72E4;
    outline: none;
    border: none;
    padding: 1em;
	background-color: white;
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

	nav ul .loginButton a:hover,
	nav ul .loginButton a:focus {
    /* I include focus because while i am developing i care about accessibility for disabled people */
    transform: translateY(-0.25rem);
    box-shadow: 0px 0px 7px -3px #010730af;
  }

	[aria-current] {
		position: relative;
		display: inline-block;
	}

	[aria-current]::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 2px;
		background-color: rgb(255,62,0);
		display: block;
		bottom: -1px;
	}

	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
	}

	.logo a{
		font-weight: 700;
		letter-spacing: 3.78px;
		font-size: 28px;
	}


	@media screen and (max-width: 920px) {

		ul {
			padding: 0;
		
		width: 90%;
		background: transparent;
		display: flex;
		justify-content: start;
		align-items: baseline;
	}

	}

	@media screen and (max-width: 500px){
		.logo a{
			font-size: 1.6em;
		}
	}


	
</style>

<nav>
	<ul>
		<li class="logo"><a href="/">şikayetvar</a></li>
		<li><a href="/">Posts</a></li> 
		

	
		<li class="loginButton"><a  href="#">LOGIN</a></li>
	</ul>
</nav>
