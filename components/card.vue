<template>
    <div class="bg-gray-800 rounded-lg overflow-hidden">
        <div class="relative h-80">
            <img :src="getLink(item.image_id)" class="absolute h-full w-full object-cover">
        </div>
        <div class="p-6">
            <h2 class="text-gray-400 overflow-hidden whitespace-nowrap">{{item.title}}</h2>
            <h3 class="text-gray-500">de {{item.artist_title}} en <span class="font-bold text-yellow-200">{{item.date_end}}</span></h3>
            <button :class="{ 'opacity-50': inCart}" class="h-10 w-full bg-gray-700 text-gray-200 rounded mt-2" @click="addToCart(item.id)">
                {{ inCart ? 'Agregado' : ' Agregar'}}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        item: {
            type: Object,
            required: true,
        },
        inCart: {
            type: Boolean,
            require: false,
            default: false,
        }
    },
    methods: {
        getLink(id) {
            return 'https://www.artic.edu/iiif/2/'+ id +'/full/843,/0/default.jpg'
        },
        addToCart(id) {
            this.$emit('add-cart', id)
        }
    }
}
</script>
