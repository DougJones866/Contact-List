<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">
      {{ detailsAreVisable ? "Hide" : "Show " }}Details
    </button>
    <ul v-if="detailsAreVisable">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
    <div class ='delete-button'>
    <button @click="$emit('delete', id)">Delete</button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: ["toggle-favorite", "delete"],
  // emits: {
  //   'toggle-favorite': function(id) {
  //     if (id) {
  //       return true;
  //     } else {
  //       console.warn('Id is missing!');
  //       return false;
  //     }
  //   },
  // },
  data() {
    return {
      detailsAreVisable: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisable = !this.detailsAreVisable;
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
    
  },
};
</script>

<style>
li {
  background-color: white;
}


</style>