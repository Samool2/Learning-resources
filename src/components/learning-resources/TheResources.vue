<template>
    <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="setStoredResButton" >Stored Resources</base-button>
    <base-button @click="setSelectedTab('add-resource')" :mode="setAddResButton" >Add Resources</base-button>
    </base-card>
    <keep-alive>
    <component :is="selectedTab"></component>
    </keep-alive>
</template>


<script>
import AddResource from './AddResource.vue';
import StoredResources from './StoredResources.vue';
export default {

    data() {
        return {
            selectedTab: 'stored-resources',

            storedResources: [
                    {
                        id: 'official-guide',
                        title: 'Official Guide',
                        description: 'The official Vue.js docs.',
                        link: 'https://vuejs.org'

                    },
                    {
                        id: 'google',
                        title: 'Google',
                        description: 'Super useful for learning anything.',
                        link: 'https://google.com'

                    }
                ]
        }
    },
    provide() {
        return {
            resources: this.storedResources,
            addResource: this.addResource,
            removeResource: this.removeResource
        }
    },
    methods: {
        setSelectedTab(resourceTab) {

            this.selectedTab = resourceTab

        },
        addResource(title, description, url) {
            const newResource = {
                id: new Date().toISOString(),
                title:title,
                description:description,
                link: url
            }
            this.storedResources.unshift(newResource);
            this.selectedTab = 'stored-resources';
        },
        removeResource(resId) {
            const refId = this.storedResources.findIndex(res => res.id === resId)
            this.storedResources.splice(refId, 1)
        }
    },
    computed:{
            setStoredResButton() {
                return this.selectedTab === 'stored-resources' ? null : 'flat';
            },
            setAddResButton() {
                return this.selectedTab === 'add-resource' ? null : 'flat';
            }

    },
    components: {

        AddResource,
        StoredResources

    }
}
</script>


<style scoped>
    button:nth-of-type(1) {
        float:right;
    }
</style>