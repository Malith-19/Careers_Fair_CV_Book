<script lang="ts">
    export let d: any = [];
    let all = [
        '190004B','190019B','190023G','190028C','190046E','190049P','190050K','190055F','190056J',
        '190058R','190061U','190064G','190077A','190081F','190086B','190088H','190093T','190097J',
        '190110V','190111B','190112E','190116U','190117A','190137J','190140L','190145G','190146K',
        '190152B','190159D','190175X','190177F','190179M','190184A','190197P','190199A','190200X',
        '190205R','190211G','190215X','190222P','190228N','190232V','190236L','190238U','190239A',
        '190241X','190242C','190249E','190253K','190257C','190277L','190282X','190283C','190287R',
        '190290U','190292D','190294K','190296T','190297X','190310J','190316H','190331A','190332D',
        '190334K','190346A','190349K','190352M','190359P','190365F','190369V','190375K','190376N',
        '190377T','190394R','190408R','190415K','190416N','190420V','190429G','190434R','190438H',
        '190451P','190453A','190458T','190471C','190478E','190482K','190483N','190488J','190493U',
        '190495D','190496G','190507U','190517B','190525X','190530H','190541R','190544E','190545H',
        '190547P','190553F','190558B','190564N','190569J','190572L','190576D','190583V','190585E',
        '190597R','190599B','190601D','190604N','190612L','190623V','190646T','190647X','190649F',
        '190650B','190653L','190658G','190676J','190686N','190690V','190697A','190705B','190707H',
        '190709P','190715F', '170032N'
    ]

    let missing: string[] = [];
    $: {
        const available = d.map(i => i.index)
        missing = all.filter(i => !available.includes(i))
    }

</script>

{#if d.length === 0}
    <div class="grid w-screen h-screen content-center">
        <h1 class="text-3xl font-bold text-center">Content API is offline</h1>
        <h4 class="text-xl text-center">Wait few minutes until it comes back online</h4>
    </div>
{:else}
    <div class="font-roboto p-[30px] my-auto mx-[20%]">
        <h1 class="text-2xl font-bold uppercase mb-3">CV Profiles [{d.length}]</h1>

        <div class="w-full bg-red-300 py-4 px-2 rounded my-3">
            <h1 class="font-bold my-1 uppercase">Missing Indexes:</h1>
            {#each missing as i}
                <span class="inline-block mr-1">{i}</span>
            {/each}
        </div>

        <div class="grid grid-cols-con ">
            {#each d as p}
                <a class="inline-block my-1" href="/{p.index}">
                    {p.index} - {p.firstName} {p.lastName}
                </a>
            {/each}
        </div>
    </div>

{/if}


<style>
    .grid-cols-con {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 1rem;
    }
</style>

