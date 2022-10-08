<script>
    import { each, onMount } from "svelte/internal";
    import BackDrop from "../components/backDrop.svelte";
    import Footer from "../components/Footer.svelte";
    import FormModal from "../components/FormModal.svelte";
    import Header from "../components/Header.svelte";
    import Result from "../components/Result.svelte";

    let showDrop = false;
    const toggoleShowDrop = ()=>{
        showDrop = !showDrop
    }

    export let urlparams;
    let email = urlparams.email;
    let regNo = urlparams.registrationNo;
    let result = []

    onMount(async () =>{
        try {
            const response = await fetch(`http://localhost:9000/result/${email}/${regNo}`)
            const data = await response.json()
            // console.log(data)
            result = data
            console.log(result)
            
        } catch (error) {
            console.log(error)
        }
    })
    
</script>


<Header  on:click={toggoleShowDrop} />

<BackDrop {showDrop}  on:click={toggoleShowDrop} >
    <FormModal />
</BackDrop>

<div class="container">
    <h1 class="h4 text-center my-5">Result Details</h1>
    <hr>

    {#if result.length  !== 0} 
    {#if result !== `result don't exist`}        

    <p class="my-1 py-1"><strong>Student Name:</strong> {result[0].studentName}</p>
    <p class="my-1 py-1"><strong>registration No:</strong> Mouau/cmp/{result[0].registrationNo}</p>
    {#if result[0].resultId.length !== 0}
    <p class="my-1 py-1"><strong>Class:</strong> {result[0].classId.className}</p>
    {:else}
    <p class="my-1 py-1"><strong>Class:</strong> Pending</p>
    {/if}

    <table class="table table-bordered table-striped shadow-lg rounded mt-3">
        <thead>
            <tr>
                <th>S/N</th>
                <th>Subject</th>
                <th>Mark</th>
            </tr>
        </thead>
       
        {#if result[0].resultId.length !== 0}
        <tbody class="table-group-divider">
           
            {#each result[0].resultId as resultSub, i }
                <Result {resultSub} {i} />
            {/each}
            

            <tr>
                <td colspan="2" class="text-center"><strong>Total Score</strong></td>
                <td><strong>150 Out of 300</strong></td>
            </tr>

            <tr>
                <td colspan="2" class="text-center"><strong>Percentage</strong></td>
                <td><strong>50%</strong></td>
            </tr>
        </tbody>
        {:else}
            <h3 class="text-center">Result Have Not Decleared For You</h3>
        {/if}
    </table>
    {:else}
    <h3 class="text-center py-5 my-5"> Result Those not Exist</h3>
    {/if}
    {/if}

    <a href="#" class="btn btn-primary py-1 px-5 mt-3" on:click = { () => window.print() }>Print</a>
    <hr>
    <a href="/" class="text-decoration-none text-dark">Back Home</a>
</div>



<Footer />

