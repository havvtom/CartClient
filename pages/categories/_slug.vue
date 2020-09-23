<template>
	<div class="container mx-auto px-6">
            <h3 class="text-gray-700 text-2xl font-medium">Wrist Watch</h3>
            <span class="mt-3 text-sm text-gray-500">200+ Products</span>
            <div 
            	class="grid gap-6 grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 mt-6"
            >
                <div 
                	class="w-full max-w-sm mx-auto rounded-md shadow-md overflow-hidden"
                	v-for="product in products"
                	:key="product.slug"
                >
                    <Product :product="product"/>
                </div>                
            </div>
            <div class="flex justify-center">
                <div class="flex rounded-md mt-8">
                    <a href="#" class="py-2 px-4 leading-tight bg-white border border-gray-200 text-blue-700 border-r-0 ml-0 rounded-l hover:bg-blue-500 hover:text-white"><span>Previous</span></a>
                    <a href="#" class="py-2 px-4 leading-tight bg-white border border-gray-200 text-blue-700 border-r-0 hover:bg-blue-500 hover:text-white"><span>1</span></a>
                    <a href="#" class="py-2 px-4 leading-tight bg-white border border-gray-200 text-blue-700 border-r-0 hover:bg-blue-500 hover:text-white"><span>2</span></a>
                    <a href="#" class="py-2 px-4 leading-tight bg-white border border-gray-200 text-blue-700 border-r-0 hover:bg-blue-500 hover:text-white"><span>3</span></a>
                    <a href="#" class="py-2 px-4 leading-tight bg-white border border-gray-200 text-blue-700 rounded-r hover:bg-blue-500 hover:text-white"><span>Next</span></a>
                </div>
            </div>
    </div>
</template>

<script type="text/javascript">
	export default {
		data () {
			return {
				products: []
			}

		},

		async asyncData ({ app, params }) {
			let response = await app.$axios.$get(`products?category=${params.slug}`)

			return {
				products: response.data
			}

		}
	}
</script>