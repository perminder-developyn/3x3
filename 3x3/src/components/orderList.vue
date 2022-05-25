<template>
<tr>
					<th>Item</th>
					<th>Price</th>
					<th>Item quantity</th>
                    <th>Add/Remove</th>
				</tr>
                <tr v-for="(row, index) in items" :key="index">
					<td>{{ row["name"] }}</td>
					<td>£{{ row["price"] }}</td>
                    <td> {{ row["count"] }}</td>
                    <button @click="add(index)">+</button>
                    <button @click="remove(index)">-</button>
				</tr>
                <tfoot>
                    <tr v-if="rounded>0">Total:£{{rounded}}</tr>
                    
                </tfoot>
</template>



<script>
export default {
    data(){
        return {
            items:[
                {
                    name: "Apples",
                    price: "1.99",
                    count: 0
                },
                {
                    name: "Butter",
                    price: "2.50",
                    count: 0
                },
                {
                    name: "Chicken",
                    price: "3.99",
                    count: 0
                },
                {
                    name: "Dumplings",
                    price: "4.00",
                    count: 0
                },
            ],
            total: 0,
            rounded: 0
        }
    },
    methods: {
        // cannot figure out how to return value then call subTotal without using setTimeout
        add(row){
            setTimeout(this.subTotal, 1)
            return (Object.values(this.items)[row].count)++
        },
        remove(row){
            setTimeout(this.subTotal, 1)
            if((Object.values(this.items)[row].count)>0)
            return (Object.values(this.items)[row].count)--
        },
        subTotal(){
            this.total = 0
            this.items.forEach(val => {
                this.total += Number(val.price*val.count);
                this.rounded =  parseFloat(this.total).toFixed(2)
            })
        }
    }
}
</script>





<style>
</style>