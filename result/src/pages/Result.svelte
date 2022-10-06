<script>
    import BackDrop from "../components/backDrop.svelte";
    import Footer from "../components/Footer.svelte";
    import FormModal from "../components/FormModal.svelte";
    import Header from "../components/Header.svelte";

    let showDrop = false;
    const toggoleShowDrop = ()=>{
        showDrop = !showDrop
    }
    
</script>


<Header  on:click={toggoleShowDrop} />

<BackDrop {showDrop}  on:click={toggoleShowDrop} >
    <FormModal />
</BackDrop>

<div class="container">
    <h1 class="h4 text-center my-5">Result Details</h1>
    <hr>
    <p class="my-1"><strong>Student Name:</strong> Peter Obi</p>
    <p class="my-1"><strong>registration No:</strong> Mouau/cmp/90608</p>
    <p class="my-1"><strong>Mark:</strong> 90</p>

    <table class="table table-bordered table-striped shadow-lg rounded">
        <thead>
            <tr>
                <th>S/N</th>
                <th>Subject</th>
                <th>Mark</th>
            </tr>
        </thead>
       
        <tbody class="table-group-divider">
            <tr>
                <td>1</td>
                <td>Mathematics</td>
                <td>98</td>
            </tr>

            <tr>
                <td>2</td>
                <td>English Language</td>
                <td>93</td>
            </tr>

            <tr>
                <td>3</td>
                <td>Physcis</td>
                <td>91</td>
            </tr>

            <tr>
                <td colspan="2" class="text-center"><strong>Total Score</strong></td>
                <td><strong>150 Out of 300</strong></td>
            </tr>

            <tr>
                <td colspan="2" class="text-center"><strong>Percentage</strong></td>
                <td><strong>50%</strong></td>
            </tr>
        </tbody>
    </table>

    <a href="#" class="btn btn-primary py-1 px-5" on:click = { () => window.print() }>Print</a>
    <hr>
    <a href="/" class="text-decoration-none text-dark">Back Home</a>
</div>



<Footer />

