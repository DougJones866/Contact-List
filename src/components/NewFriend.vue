<template>
  <form @submit.prevent="submitData">Enter Contact Information
    <div>
      <label>Name</label>
      <input type="text" v-model="enteredName"/>
    </div>
    <div>
      <label>Phone Number</label>
      <input type="tel" v-model="enteredPhone" />
    </div>
    <div>
      <label>E-Mail</label>
      <input type="email" v-model="enterdEmail"/>
    </div>
    <div>
        <button>Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
    emits: ['add-contact'],
    data() {
        return {
            enteredName: '',
            enteredPhone: '',
            enteredEmail: '',
        }
    },
    methods: {
        submitData() {
            this.$emit('add-contact', this.enteredName, this.enteredPhone, this.enteredEmail);
        }
    }
};
</script>

<style>
form {
  background-color: white;
}
</style>