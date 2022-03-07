<script>
    // @ts-ignore
    import {sum} from 'd3-array';
    import {csv} from 'd3-fetch';

    const WORLD_CODE = 'OWID_WRL'

    //throw `TODO utiliser les autres données`

    csv('static/data/annual-co2-emissions-per-country.csv')
    .then(rows => {
        const worldRows = rows
            .filter(({Code}) => Code === WORLD_CODE)
            .map( ({Year, "Annual CO2 emissions": CO2emissions}) => ({
                Year: Number(Year),
                CO2emissions: Number(CO2emissions),
            }) )
        
        console.log('worldRows', worldRows)

        console.log('somme', sum(worldRows.map( ({CO2emissions}) => CO2emissions )))

    })

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

<p class="methodology-credit">Sources de données : 
    https://ourworldindata.org/grapher/annual-co2-emissions-per-country?tab=chart&country=~OWID_WRL
    J'ai cliqué sur "download" le 27 décembre 2021 et téléchargé le csv. Je n'utilise que les données agregées "World" (monde entier) 
    et j'ignore les données spécifiques des pays
    
    ourworldindata utilise les données du Global Carbon Budget https://doi.org/10.18160/gcp-2021
    Si j'ai bien compris, ces données sont sous licence CC-BY et un bloc 
    illisible de noms de personnes à citer est ici : https://essd.copernicus.org/preprints/essd-2021-386/
    
    Les données téléchargées depuis ourworldindata ont été retraitées
    Tout est sur github je crois https://github.com/owid
    et j'ai la flemme de retrouver le chemin
    
    </p>


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

    .methodology-credit{
        margin-top: 4rem;
        color: #444;
        font-size: 0.8em;
    }


</style>

