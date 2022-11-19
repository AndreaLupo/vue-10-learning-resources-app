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
        resources: this.storedResources
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
    }

  }
}
</script>

<style>

</style>