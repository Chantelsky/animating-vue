<template>
  <div>
    <div class="input">
      <input type="text" v-model="newContact" placeholder="Name" />
      <button @click="addContact">Add Contact</button>
      <button @click="sortContacts">Sort Contacts</button>
    </div>

    <transition-group name="slide-up" tag="ul">
      <li v-for="contact in contacts" :key="contact">{{ contact }}</li>
    </transition-group>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newContact: '',
      contacts: ['Beau Thabeast', 'Cindy Rella', 'Alice Vunderlind']
    }
  },
  methods: {
    addContact() {
      this.contacts.push(this.newContact)
      this.newContact = ''
    },
    sortContacts() {
      this.contacts.sort()
    }
  }
}
</script>

<style>
.input {
  display: flex;
  justify-content: center;
  align-items: center;
}

input {
  width: 20%;
  height: 20px;
}

button {
  width: 120px;
}

.slide-up-enter {
  opacity: 0;
  transform: translateY(10px);
}

.slide-up-enter-active {
  transition: all 0.2s ease;
}

.slide-up-move {
  transition: transform 0.5s ease-out;
}
</style>