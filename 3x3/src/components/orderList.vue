<template>
<tr>
					<th>Item</th>
					<th>Price</th>
					<th>Item quantity</th>
                    <th>Add/Remove</th>
				</tr>
                <tr v-for="(row, index) in items" :key="index">
					<td>{{ row["name"] }}</td>
					<td>{{ row["price"] }}</td>
                    <td> {{ row["count"] }}</td>
                    <button @click="add(index)">+</button>
                    <button @click="remove(index)">-</button>
				</tr>
                <tfoot>
                    <tr>Total: {{total}} <button @click="subTotal()">Calculate</button></tr>
                    
                </tfoot>
</template>



<script>
export default {
    data(){
        return {
            items:[
                {
                    name: "a",
                    price: 1,
                    count: 0
                },
                {
                    name: "b",
                    price: 2,
                    count: 0
                },
                {
                    name: "c",
                    price: 3,
                    count: 0
                },
                {
                    name: "d",
                    price: 4,
                    count: 0
                },
            ],
            total: 0
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
            })
        }
    }
}
</script>





<style>
</style>