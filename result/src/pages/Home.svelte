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

	const prepareResult = (e) =>{
		let email = e.detail.email
		let regNo = e.detail.regNo
		if((email === undefined || email === '' ) || (regNo === undefined || regNo === null)){
			alert("please fill in your details")
		}else{
			window.location.assign(window.location.href + `result/${email}/${regNo}`)
		}
	}

</script>

<Header on:click={toggoleShowDrop} />

<BackDrop {showDrop} on:click={toggoleShowDrop} >
	<FormModal on:sendE_RegNo={prepareResult}  />
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