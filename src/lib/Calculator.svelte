<script>
    let fuelPrice

    let amount
    let unit
    
    let errorMessage

    const calculateUnit = () => {
        if(!fuelPrice){
            errorMessage = "Please enter the Fuel Price"
            return
        }

        if(!amount){
            errorMessage = "Please enter the amount for fuel"
            return
        }


        unit = Math.round( amount / fuelPrice)
        errorMessage = false
    }

    const calculateAmount = () => {
        if(!fuelPrice){
            errorMessage = "Please enter the Fuel Price"
            return
        }

        if(!unit){
            errorMessage = "Please enter the amount of fuel"
            return
        }

        amount = Math.round(unit * fuelPrice)
        errorMessage = false
    }

</script>

<div class="container">

    <!-- Row 1 -->
    <div class="columns is-centered is-mobile">
        <div class="column is-one-half">
            <div class="field">
                <div class="control has-floating-label">
                    <input class="input is-medium with-floating-label is-link mt-2" name="fuelPrice" type="number" placeholder=" " bind:value={fuelPrice}>
                    <label class="label is-medium is-floating-label has-text-grey" for="referenceWidth">Fuel Price</label>
                </div>
            </div>
        </div>
    </div>

    <!-- Row 2 -->
    <div class="columns is-centered">
        <div class="column is-one-half">
            <div class="field">
                <div class="control has-floating-label">
                    <input class="input is-medium with-floating-label is-link mt-2" type="number" name="referenceHeight" placeholder=" " bind:value="{amount}" on:blur={calculateUnit}>
                    <label class="label is-medium has-text-grey is-floating-label" for="referenceHeight">Amount</label>
                </div>
            </div>
        </div>
        <div class="column is-one-half">
            <div class="field">
                <div class="control has-floating-label">
                    <input class="input is-medium with-floating-label is-link mt-2" type="number" name="referenceHeight" placeholder=" " bind:value="{unit}" on:blur={calculateAmount}>
                    <label class="label is-medium has-text-grey is-floating-label" for="referenceHeight">Fuel Unit</label>
                </div>
            </div>
        </div>
    </div>
    
    {#if errorMessage }
        <p class="p-2 tag is-danger is-medium">{errorMessage}</p>
    {/if}
</div>


