<div class="grid-component">
    <div class="items-list">
		<th>Item</th>
		<th>Price</th>
		<th>Item quantity</th>
        <th>Add/Remove</th>
        {#each items as item,index}
            <tr class="quantity">
			    <td>{ item.name }</td>
			    <td>£{ item.price }</td>
                <td> { item.count }</td>
                <button on:click={()=>add(index)}>+</button>
                <button on:click={()=>remove(index)}>-</button>
		    </tr>
        {/each}
        <tfoot class="total">
            {#if rounded > 0}
                <tr>Total:£{rounded}</tr>
            {/if}
        </tfoot>
    </div>
</div>

<script>
let rounded = 0;
let total = 0;
let items = [
    {
        name: 'Apples',
        price: '1.99',
        count: 0
    },
    {
        name: 'Butter',
        price: '2.50',
        count: 0
    },
    {
        name: 'Chicken',
        price: '3.99',
        count: 0
    },
    {
        name: 'Dumplings',
        price: '4.00',
        count: 0
    },

];
 
function add(index){
        ((items)[index].count)++
        subTotal()
}
function remove(index){
        if (((items)[index].count)>0)
            ((items)[index].count)--
        subTotal()
}

$: rounded = parseFloat(total).toFixed(2)

function subTotal(){
    total = 0
    items.forEach(val => {
        total += Number(val.price*val.count);
    })
}
</script>

<style>
.quantity {
    text-align: center;
}
th {
    padding: .5rem;
    border-bottom: 3px solid black;
    border-top: 1px solid black;
    border-left: 1px solid black;
    border-right: 1px solid black;
}
td {
    padding-top: .5rem;
    border: 1px solid rgba(128, 128, 128, 0.133);
}
.total {
    background-color: rgba(0, 255, 255, 0.153);
    transform: translateY(1rem) translateX(15rem);
}
.grid-component{
        padding: 2rem;
}

</style>