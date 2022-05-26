<template>
  <div class="grid-component">
    <button
      class="toggle" 
      v-on:click="toggle()"
      >grid/list</button>
    
        <input 
          type="text"
          v-model="search"
          placeholder="Search title.." 
          v-on:keyup="filteredList()"/>
        
           <div id="list-container"> 
             <li  
                id="item-list" 
                v-for="(item, index) in items" 
                :key="index" >
                    <div v-if="item.display">
                       <div v-if="list"> 
                        {{ item.title }} 
                       </div>
                       <img v-bind:src="item.image">
                    </div>
              </li>
            </div>
    </div>
</template>


<script>
  export default{
    data() {
      return {
        search: '',
        list: false,
        items: [
          { title: 'Tekken 3', image:"https://upload.wikimedia.org/wikipedia/en/thumb/f/f0/T3usposter.jpg/220px-T3usposter.jpg", display:true},
          { title: 'Counter Strike: Source', image:"https://upload.wikimedia.org/wikipedia/en/4/43/Counter-Strike_Source_%28box_art%29.jpg", display:true},
          { title: 'Fifa', image:"https://upload.wikimedia.org/wikipedia/en/d/d4/FIFA95_coverart.jpg", display:true},
          { title: 'Leauge of Legends', image:"https://thumbnails.pcgamingwiki.com/4/40/League_of_Legends_-_cover.jpg/300px-League_of_Legends_-_cover.jpg", display:true},
          { title: 'Counter Strike: Global Offensive', image:"https://upload.wikimedia.org/wikipedia/en/6/6e/CSGOcoverMarch2020.jpg", display:true},
          { title: 'Halo Infinite', image:"https://upload.wikimedia.org/wikipedia/en/1/14/Halo_Infinite.png", display:true},
          { title: 'EuroTruck Simulator 2', image:"https://upload.wikimedia.org/wikipedia/en/0/0e/Euro_Truck_Simulator_2_cover.jpg", display:true},
          { title: 'Call of Duty', image:"https://upload.wikimedia.org/wikipedia/en/f/f3/Call_of_Duty_%282003%29_cover.jpg", display:true},
          { title: 'Pro-Evolution  Soccer', image:"https://upload.wikimedia.org/wikipedia/en/3/31/Pro_Evolution_Soccer.jpg", display:true}
              ]
             }
           },
  methods:{
      filteredList() {
          return this.items.filter(item => {
            const characters = Object.values(item.title).toString()
            if(characters.toLowerCase().includes(this.search)){
              item.display = true;
              console.log(this.search)
              }else{
                item.display = false;
                   }
                  })  
                },
    toggle(){
      if(document.getElementById("list-container")){
        document.getElementById("list-container").setAttribute("id", "grid-list");
        this.list = true;
      }else{
        document.getElementById("grid-list").setAttribute("id", "list-container")
        this.list = false;
      }
    }

}
}
</script>


<style>
li{
    list-style: none;
}
img{
   border-radius: 1rem;
    max-width: 150px;
}
#list-container{
  display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
}

#item-list{
 flex: 1 1 30%;
 padding-top: 4rem;
}

#item-grid{
   display: inline;
   padding-top: 4rem;
}

  

</style>