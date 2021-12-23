<script>
    // @ts-ignore
    import {sum} from 'd3-array';

    let co2PerYear = {
        "2021": 10,
        "2020": 8,
        "2019": 6,
        "2018": 4,
        "2017": 2,
        "2016": 1
    }

    const entries = [...Object.entries(co2PerYear)]

    const total = sum(entries.map(([year, co2quantity]) => co2quantity))

</script>

<h1>CO2-left</h1>
<p>La quantité de CO<sub>2</sub> déja dans l'atmosphère et le budget restant</p>

<div class="co2-budget">
    {#each entries as [year, co2quantity]}	
    <div style={`width: ${co2quantity*100/total}%;`} title={year}>{year}</div>
	{/each}
</div>

<style lang="scss">
    
    $diag-height: 3rem;

    .co2-budget{
        display: flex;
        flex-direction: row;
        height: $diag-height;
        width: 100%;

        > div{
            height: 100%;
            border: 1px solid grey;
            border-right-width: 0;

            background-color: blanchedalmond;
            line-height: $diag-height;
            text-align: center;

            &:last-of-type{
                border-right-width: 1px;
            }
        }
    }



</style>

