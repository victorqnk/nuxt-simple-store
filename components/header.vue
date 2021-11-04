<template>
    <div class="max-w-full mx-auto">
      <div class="flex justify-between">
        <h1 class="flex text-2xl text-yellow-400 mb-12">{{ title }} <span class="text-green-400 font-light">{{subtitle}}</span></h1>
        <div class="flex" @click="reset">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" viewBox="0 0 20 20" fill="text-green-400">
            <path fill-rule="evenodd" d="M10 2a4 4 0 00-4 4v1H5a1 1 0 00-.994.89l-1 9A1 1 0 004 18h12a1 1 0 00.994-1.11l-1-9A1 1 0 0015 7h-1V6a4 4 0 00-4-4zm2 5V6a2 2 0 10-4 0v1h4zm-6 3a1 1 0 112 0 1 1 0 01-2 0zm7-1a1 1 0 100 2 1 1 0 000-2z" clip-rule="evenodd" />
          </svg>
          <span class="text-gray-300">{{cart}}</span>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    props: {
        cart: {
            type: String,
            required: true,
        },
    },
    data() {
        return {
            title: 'Quo',
            subtitle: 'nuxt',
        }
    },
    methods: {
        reset() {
            this.$emit('clear', true)
        }
    }
}
</script>