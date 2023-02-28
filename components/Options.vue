<template>
     
        <div class="flex flex-col w-4/5 m-auto">
            <div class="flex flex-row p-10 m-auto items-center w-fit ">
                        <button  v-on:click="form1isShow = !form1isShow, form2isShow = false" class="flex flex-col text-zinc-400 text-center w-32 h-32 m-3 items-center p-3 border-zinc-400 border-solid border-2 rounded opacity-70 hover:opacity-100">
                          <img class="w-10 h-10 m-2" src="/icons/icons8-economic-quantity-32.png" alt="" srcset="">
                          <p> <strong> Quantity</strong></p>
                     </button>
                 <button v-on:click="form2isShow = !form2isShow, form1isShow = false" class="flex flex-col text-zinc-400 text-center w-32 h-32 m-3 items-center p-3 border-zinc-400 border-solid border-2 rounded opacity-70 hover:opacity-100">
                          <img class="w-10 h-10 m-2" src="/icons/icons8-picture-50.png" alt="" srcset="">
                          <p><strong>Image with text</strong></p>
                 </button>
                </div>
                <div v-show="form1isShow" class="bg-zinc-200 p-6 rounded mb-3 m-auto w-1/2">
                   <form @submit.prevent="addImageWithText">
                    <h4>New Product</h4>
                    <div class="mb-6">
                        <label for="ImageURL" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Image link</label>
                        <input  id="ImageURL" v-model="ImageURL" type="text" name="ImageURL" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                    </div>
                    <div class="mb-6">
                            <label for="ImageText" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Image text</label>
                            <input  id="ImageText" v-model="ImageText" type="text" name="ImageText" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                    </div>
                        <button type="submit" value="Submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Add image</button>
                </form>
                <div class="grid grid-cols-3 gap-2 w-fit m-auto p-4">
                      <div class="p-3 rounded text-center text-zinc-700 bg-white border-2 border-zinc-400" v-for="item in Imagelist" v-bind:key="item.id">
                            <img class=" w-full h-32 object-cover" :src="item.ImageURL" alt="" srcset="">
                            <p><strong>{{ item.ImageText }}</strong></p>
                            <button v-bind:key="item.id" @click="deleteImageWithText(item.id)" type="button" value="Delete" class="text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-yellow-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-800">Delete</button>
                          </div>
                    
                    </div>
                    </div>
           <div v-show="form2isShow" class="bg-zinc-200 p-6 rounded mb-3 m-auto w-1/2">
            <form @submit.prevent="addQuantityWithDiscount">
                        <h4>New Product</h4>
                        <div class="mb-6">
                            <label for="Quantity" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Quantity</label>
                            <input  id="Quantity" v-model="Quantity" type="text" name="Quantity" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                        </div>
                        <div class="mb-6">
                                <label for="DiscountRate" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Discounte rate</label>
                                <input  id="DiscountRate" v-model="DiscountRate" type="text" name="DiscountRate" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                        </div>
                            <button type="submit" value="Submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Add quantity</button>
                    </form>
                    <table class="table-auto mt-6">
                        <tr class="">
                            <th class="pr-6">Quantity</th>
                            <th lass="pr-6">Discounte rate</th>
                            <th lass="pl-6">   </th>
                        </tr>
                          <tr class=" " v-for="item in Quantitylist" v-bind:key="item.id">
                               <td lass="pr-6"><strong>{{ item.Quantity }}</strong></td>
                                <td class="pr-6">{{ item.DiscountRate }}</td>
                                <td class="pl-6"> <button v-bind:key="item.id" @click="deleteQuantityWithDiscount(item.id)" type="button" value="Delete" class="text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-yellow-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-800">Delete</button></td>
                                
                          </tr>
                    
                        </table>
           </div>
            
        
        </div>
</template>
<script>

export default {
    data() {
        return {
            ImageURL: '',
            ImageText: '',
            Quantity: '',
            DiscountRate: '',
            Imagelist:undefined,
            Quantitylist: undefined,
            form1isShow: false,
            form2isShow: false,
            errors: []
        }
    },
    mounted() {
        this.$api.get('/ImagesWithText')
            .then((resp) => {
                this.Imagelist = resp.data;
                console.log(resp.data);
            }),
            this.$api.get('/QuantityWithDIscount')
                .then((resp) => {
                    this.Quantitylist = resp.data;
                    console.log(resp.data);
                })
    },

    methods: {
        addImageWithText() {
        this.$api.post('/ImagesWithText' , {ImageURL: this.ImageURL, ImageText: this.ImageText} )
                .then((Response) => {
                    this.$api.get('/ImagesWithText')
                        .then((resp) => {
                            this.Imagelist = resp.data;
                            console.log(resp.data);
                        })
                .catch((err) => {
                    this.errors.push(err)
                });
                this.ImageURL='';
                this.ImageText = '';
                
            })
        },
        addQuantityWithDiscount() {
            this.$api.post('/QuantityWithDiscount', { Quantity: this.Quantity, DiscountRate: this.DiscountRate })
                .then((Response) => { 
                     this.$api.get('/QuantityWithDIscount')
                        .then((resp) => {
                            this.Quantitylist = resp.data;
                            console.log(resp.data);
                        })
                })
                .catch((err) => {
                    this.errors.push(err)
                });
            this.Quantity = '';
            this.DiscountRate = '';
             
        },
        deleteImageWithText(id) {
            this.$api.delete('/ImagesWithText/' + id)
                .then(response => {
                    this.$api.get('/ImagesWithText')
                        .then((resp) => {
                            this.Imagelist = resp.data;
                            console.log(resp.data);
                        })
                });
                
            },
            deleteQuantityWithDiscount(id) {
            this.$api.delete('/QuantityWithDiscount/' + id)
                .then(response => {
                    this.$api.get('/QuantityWithDiscount')
                        .then((resp) => {
                            this.Quantitylist = resp.data;
                            console.log(resp.data);
                        })
                });

        },
    },
   
       
}
</script>