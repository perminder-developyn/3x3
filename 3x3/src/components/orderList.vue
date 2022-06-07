<template>
    <div class="grid-component">
        <div class="items-list">
            <tr>
				<th> Item </th>
				<th> Price </th>
				<th> Item quantity </th>
                <th> Add/Remove </th>
			</tr>
            <tr v-for="(row, index) in items" :key="index">
				<td> {{ row["name"] }} </td>
				<td>£{{ row["price"] }} </td>
                <td> {{ row["count"] }} </td>
                <button @click="add(index)"> + </button>
                <button @click="remove(index)"> - </button>
			</tr>
            <tfoot class="total">
                <tr v-if="rounded>0"> Total:£{{rounded}} </tr>
            </tfoot>
        </div>
    </div>
</template>



<script>
export default {
    data(){
        return {
            total: 0,
            rounded: 0,
            items:[
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
            ]
        }
    },
    methods: {
        add(row){
            setTimeout(this.subTotal, 1)
            return (this.items)[row].count++;
        },
        remove(row){
            setTimeout(this.subTotal, 1)
            if((this.items)[row].count>0)
            return (this.items)[row].count--;
        },
        subTotal(){
            this.total = 0
            this.items.forEach(val => {
                this.total += Number(val.price*val.count);
                this.rounded =  parseFloat(this.total).toFixed(2);
            })
        }
    }
}
</script>

<style>
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
</style>