<template>
    <div class="grid-component">
        <button 
            class="toggle"
            v-on:click="layoutToggle()"
        >
            Game: {{ layout }}
        </button>


        <input 
            type="text"
            v-model="search"
            placeholder="Search games.." 
            v-on:keyup="filteredList()"
        />
        <div id="game-list-container">
            <ul v-if="layout === 'grid'" class="grid">
                <li   
                    v-for="(item, index) in items" 
                    :key="index"
                >
                    <div v-if="item.display" class="content">
                        <h3>{{ item.title }}</h3> 
                        <img v-bind:src="item.image">
                    </div>     
                </li>
            </ul > 
            <ul v-if="layout === 'list'" class="list">
                <li   
                    v-for="(item, index) in items" 
                    :key="index"
                >
                    <div v-if="item.display" class="content">
                        <img v-bind:src="item.image">
                    </div>   
                </li>
            </ul> 
        </div>
    </div>
</template>


<script>
    export default{
        data() {
            return {
                search: '',
                layout: 'grid',
                items: [
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
            }
        },
        methods: {
            filteredList() {
                this.items.filter(item => {
                    item.display = item.title.toLowerCase().includes(this.search);
                });
            },
            layoutToggle() {
                this.layout === 'grid' ? this.layout = 'list' : this.layout = 'grid';
            }
        }
}
</script>


<style>
li {
    list-style: none;
}
img {
    border-radius: 1rem;
    max-width: 100px;
}
li h3 {
    max-width: 150px;
}

.content {
    padding: 1rem;

}
.grid {
    display: flex;
    flex-wrap: wrap;
    max-width: 45rem;
}

</style>