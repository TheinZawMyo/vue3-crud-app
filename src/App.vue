<template>
  <div class="container mt-4">
    <h1>Vue 3 CRUD Example</h1>
    <UserForm @add-user="addUser" :edit-user="editData" @update-user="updateUser" />
    <UserList :users="users" @edit="setEditUser" @delete="deleteUser" />
  </div>
</template>

<script>
import UserForm from './components/UserForm.vue';
import UserList from './components/UserList.vue';

export default {
  components: { UserForm, UserList },
  data() {
    return {
      users: [],
      editData: null,
    };
  },
  methods: {
    addUser(user) {
      user.id = Date.now();
      this.users.push(user);
    },
    setEditUser(user) {
      this.editData = { ...user };
    },
    updateUser(updatedUser) {
      const index = this.users.findIndex((u) => u.id === updatedUser.id);
      if (index !== -1) this.users[index] = updatedUser;
      this.editData = null;
    },
    deleteUser(userId) {
      this.users = this.users.filter((user) => user.id !== userId);
    },
  },
};
</script>
