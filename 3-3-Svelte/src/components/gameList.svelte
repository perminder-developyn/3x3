<div class="grid-component">
    <button
      class="toggle" 
      on:click={toggle}
      >grid/list
    </button>
    
    <input 
      type="text"
      bind:value={search}
      placeholder="Search title.." 
      on:keyup={filteredList}/>
    <div id="list-container">   
      {#each items as item}
        {#if item.display}
        <li id="item-list">
          {#if list}
            {item.title}
          {/if}
          <img src={item.image} alt={item.title}/>
        </li>
        {/if}
      {/each}
    </div>
</div>

   <script>
let search = '';
let list = false;
let items = [
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

function filteredList() {
  return items.forEach(item => {
    if(item.title.includes(search)){
       item.display = true;
       console.log(search, items)
    }else{
       item.display = false;
      }
    })  
};

function toggle(){
  if(document.getElementById("list-container")){
    document.getElementById("list-container").setAttribute("id", "item-grid");
    list = true;
    }else{
    document.getElementById("item-grid").setAttribute("id", "list-container")
    list = false;
    }
}
</script>


<style>
    .grid-component {
      flex: 1 1 30%; 
      margin: 5px; 
      padding: 2rem;
    }
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