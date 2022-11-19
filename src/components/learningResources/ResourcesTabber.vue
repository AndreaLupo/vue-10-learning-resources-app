<template>
  <base-card>
    <base-button @click="selectTab('stored-resources')" :mode="storedResButtonMode">
        Stored resources
    </base-button>
    <base-button @click="selectTab('add-resource')" :mode="addResButtonMode">
        Add resource
    </base-button>
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
        // equals to the tag of the component I want to show within component tag
        selectedTab: 'stored-resources',
        storedResources: [
            { 
                id: 'official-guide',
                title: 'Official Guide',
                description: 'The official Vue.js documentation',
                link: 'https://vuejs.org'
            },
            { 
                id: 'google',
                title: 'Google',
                description: 'Well, it\'s Google!',
                link: 'https://google.com'
            }
        ]
    };
  },
  provide() {
    return {
        resources: this.storedResources,
        addResource: this.addResource,
        deleteResource: this.deleteResource
    };
  },
  computed: {
    storedResButtonMode() {
        return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
        return this.selectedTab === 'add-resource' ? null : 'flat';
    }
  },
  methods: {
    selectTab(tab) {
        this.selectedTab = tab;
    },
    addResource(title, description, link) {
      console.log(title, description, link);
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link 
      };
      this.storedResources.unshift(newResource);
      this.selectTab('stored-resources');
    },
    deleteResource(resourceId) {
      const resIndex = this.storedResources.findIndex(res => res.id === resourceId);
      this.storedResources.splice(resIndex, 1);
    }


  }
}
</script>

<style>

</style>