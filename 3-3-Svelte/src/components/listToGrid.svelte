<div class="grid-component">
    <button
        class="toggle" 
        on:click={toggle}
    >
        Game: {layout}
    </button>
    
    <div id="list-container">
        <div id="item-grid">
            {#if layout==='grid'}
                {#each items as item}
                    <li>
                        <img src={item.image} alt={item.title}/>
                    </li>
                {/each}
            {/if}
        </div>
        {#if layout==='list'}
           {#each items as item}
                <li>
                    <h3>{item.title}</h3>
                    <img src={item.image} alt={item.title}/>
                </li>
            {/each}
        {/if}
    </div>
</div>

<script>
let layout = 'grid';
let items = [
    { 
        title: 'Tekken 3', 
        image: 'https://upload.wikimedia.org/wikipedia/en/thumb/f/f0/T3usposter.jpg/220px-T3usposter.jpg',
        display: true
    },
    { 
        title: 'Counter Strike: Source', 
        image: 'https://upload.wikimedia.org/wikipedia/en/4/43/Counter-Strike_Source_%28box_art%29.jpg', 
        display: true
    },
    { 
        title: 'Fifa', 
        image: 'https://upload.wikimedia.org/wikipedia/en/d/d4/FIFA95_coverart.jpg', 
        display: true
    },
    { 
        title: 'Leauge of Legends', 
        image: 'https://thumbnails.pcgamingwiki.com/4/40/League_of_Legends_-_cover.jpg/300px-League_of_Legends_-_cover.jpg', 
        display: true
    },
    { 
        title: 'Counter Strike: Global Offensive', 
        image: 'https://upload.wikimedia.org/wikipedia/en/6/6e/CSGOcoverMarch2020.jpg', 
        display: true
    },
    { 
        title: 'Halo Infinite', 
        image: 'https://upload.wikimedia.org/wikipedia/en/1/14/Halo_Infinite.png', 
        display: true
    },
    { 
        title: 'EuroTruck Simulator 2', 
        image: 'https://upload.wikimedia.org/wikipedia/en/0/0e/Euro_Truck_Simulator_2_cover.jpg', 
        display: true
    },
    { 
        title: 'Call of Duty', 
        image: 'https://upload.wikimedia.org/wikipedia/en/f/f3/Call_of_Duty_%282003%29_cover.jpg', 
        display: true
    },
    { 
        title: 'Pro-Evolution  Soccer', 
        image: 'https://upload.wikimedia.org/wikipedia/en/3/31/Pro_Evolution_Soccer.jpg', 
        display: true
    }
]



const toggle = () => {
    layout === 'grid' ? layout = 'list' : layout = 'grid';
}
</script>


<style>
.toggle {
    float: right;
}

li {
    list-style: none;
    padding-top: 2rem;
    margin-top: 2rem;
}

img {
    border-radius: 2rem;
    max-width: 150px;
    padding: 1rem;
}

li h3 {
    max-width: 150px;
}

#item-grid {
    display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	grid-template-rows: 1fr 1fr 1fr;
} 

.grid-component {
    padding: 2rem;
}
</style>