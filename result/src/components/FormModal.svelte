<script>
    import { createEventDispatcher } from "svelte/internal";


    let email;
    let regNo;

    const dispatcher = createEventDispatcher()
    let formInput;

    const resultLogDetails = () =>{
        formInput = {email,regNo}
        dispatcher('sendE_RegNo',formInput)
    }

</script>

<h1 class="h4 text-center fs-5 bg-primary rounded-pill py-2 text-white">Check Result</h1>

<form on:submit|preventDefault={resultLogDetails}>

    <div class="form-group py-1">
        <label for="">Email Address</label>
        <input type="email" class="form-control" bind:value={email} placeholder="Enter your Email Address">
    </div>
    <br>

    <div class="form-group py-1">
        <label for="">Registration No.</label>
        <input type="number" class="form-control" bind:value={regNo} placeholder="Enter your Registration Number">
    </div>
    <br>
    

    <button class="btn btn-primary">Submit</button>
</form>