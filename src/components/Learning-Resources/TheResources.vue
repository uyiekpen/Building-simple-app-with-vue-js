<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButton"
      >stored resources</base-button
    >

    <base-button @click="setSelectedTab('add-resource')" :mode="addResButton"
      >Add resources</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Officail Guide ',
          description: 'the officail Vue.js Documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'the officail search page',
          link: 'https://google.com',
        },
      ],
    };
  },

  provide() {
    return {
      resources: this.storedResources,
      addInputResources: this.addInputResources,
      deleteResources: this.removeResource,
    };
  },

  computed: {
    storedResButton() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },

    addResButton() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addInputResources(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };

      this.storedResources.unshift(newResource);

      this.selectedTab = 'stored-resources';
    },
    removeResource(resId) {
      const resIndex = this.storedResources.findIndex((res) => res.id == resId);

      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>
