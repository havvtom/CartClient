<template>
	<div class="bg-white flex items-center">
		<div class="container flex items-center flex-wrap lg:flex-no-wrap">
			<nuxt-link
				:to="{ name: 'index' }"
				class="mr-10"
			>
				<img src="~/assets/logo.svg" class="h-12">
			</nuxt-link>
			<div class="flex w-full justify-between">
				<ul class="lg:h-24 lg:flex items-center">
					<li v-for="(category, index) in categories" :key="index">
					<div class="p-10">
		  				<div class="dropdown inline-block relative">
		    				<nuxt-link 
		    					:to="{ 
		    						name: 'categories-slug',
		    						params: {
			    						slug: category.slug
			    					}
		    					}" 
		    					class="text-gray-700 text-lg py-2 px-4 rounded inline-flex items-center hover:text-gray-500">
		      				<span class="mr-1">{{category.name}}</span>
		      
		    				</nuxt-link>
				    		<ul v-if="category.children.data.length" class="dropdown-menu absolute origin-top-right right-0 hidden text-gray-700 pt-1 bg-white shadow-xs">
							    <li 
							    	class=""
							    	v-for="child in category.children.data"
							    	:key="child.slug"
							    >
							      	<nuxt-link 
							      		:to="{ 
							      			name: 'categories-slug',
							      			params: {
								      			slug: child.slug
								      		}
							      		}"
							      		class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900 whitespace-no-wrap" 
							      	>
						      			{{ child.name }}
						      		</nuxt-link>
						  		</li>				      	
				    		</ul>
		  				</div>
					</div>
					</li>
					<li>
						<nuxt-link
							:to="{
								name: 'index'
							}"
							class="text-lg text-gray-700 lg:py-8 lg:px-4 hover:text-gray-500"
						>
							Search
						</nuxt-link>
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script type="text/javascript">
	import { mapGetters } from 'vuex'
	export default {
		computed: {
			...mapGetters({
				categories: 'categories'
			})
		}
	}
</script>