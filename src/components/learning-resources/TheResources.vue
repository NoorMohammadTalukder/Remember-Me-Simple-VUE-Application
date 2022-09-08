<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">
            Stored Resources
        </base-button>

        <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">
            Add Resources
        </base-button>
    </base-card>

    <component :is="selectedTAb">

    </component>

</template>
<script>
 import StoredResources from './StoredResources.vue';
 import AddResource from './AddResource.vue';

export default {
    components:{
        StoredResources,
        AddResource
    },

    data(){
        return{
            selectedTAb:'stored-resources',

            storedResources: [
            {
              id: 'official-guide',
              title: 'Official Guide',
              description: 'The official Vue.js documentation',
              link: 'https://vuejs.org',
            },
            {
              id: 'google',
              title: 'Google',
              description: 'Learn Google',
              link: 'https://google.org',
            },
          ],
        };
    },

    provide(){
        return{
            resources:this.storedResources,
        };
    },


    computed:{
        storedResButtonMode(){
            return this.selectedTAb==='stored-resources' ? null:'flat';
        },
        addResButtonMode(){
            return this.selectedTAb==='add-resource' ? null:'flat';
        }
    },


    methods:{
        setSelectedTab(tab){
            this.selectedTAb=tab;
        }
    }
}
</script>