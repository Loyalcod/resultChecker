<script>
    import BackDrop from "../components/BackDrop.svelte";
    import Footer from "../components/Footer.svelte";
    import FormModal from "../components/FormModal.svelte";
    import Header from "../components/Header.svelte";
	
	let showDrop = false;
		const toggoleShowDrop = () =>{
			showDrop = !showDrop
		}

let src = '../images/result1.jpeg'
</script>

<Header on:click={toggoleShowDrop} />

<BackDrop {showDrop} on:click={toggoleShowDrop} >
	<FormModal />
</BackDrop>

<img src={src} alt="Student Result Checker">

<Footer />

<style>

	img{
		display: block;
		width: 100vw;
		height: 75vh;
		object-fit: cover;
	}
	
	
</style>