<template>
	<div class="field flex flex-col mb-5">
		<label class="mb-3 text-gray-700 capitalize text-lg">
			{{ type }}
		</label>
		<div class="inline-block relative w-64">
		  <select class="block appearance-none w-full text-gray-700 bg-white border border-gray-400 hover:border-gray-500 px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline" 
		  	@change="changed($event, type)"
		  	:value="selectedVariationId"
		  >
		  	<option value="">Please choose</option>
		    <option 
		    	v-for="(product, index) in variations"
		    	:key="index"
		    	:value="product.id"
		    >
		    	{{product.name}} 

		    	<template v-if="product.price_variation">
		    			({{ product.price }})
		    	</template>
		    </option>
		  </select>
		  <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700">
		    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
		  </div>
		</div>
	</div>
</template>

<script type="text/javascript">
	export default {
		props: {
			type: {
				required: true,
				type: String
			},
			variations:{
				required: true,
				type: Array
			},
			value: {
				required: false,
				default: ''
			}
		},
		computed: {
			selectedVariationId () {
				if(!this.findVariation(this.value.id)) {
					return ''
				}

				return this.value.id
			}
		},
		methods: {
			changed (event, type) {
				this.$emit('input', this.findVariation(event.target.value))
			},
			findVariation (id) {
				let variation = this.variations.find(v => v.id == id)

				if (typeof variation === 'undefined') {
					return null
				}

				return variation
			}
		},

	}
</script>