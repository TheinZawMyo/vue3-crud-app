<template>
    <div class="mt-4">
        <div v-if="users.length">
            <h3>User List</h3>
            <div class="list-group">
                <UserCard v-for="user in users" :key="user.id" :user="user" @edit="handleEdit" @delete="handleDelete" />
            </div>
        </div>
        <p v-else>No users to display. Add some!</p>
    </div>
</template>

<script>
import UserCard from './UserCard.vue';

export default {
    components: { UserCard },
    props: {
        users: Array,
    },
    methods: {
        handleEdit(user) {
            this.$emit('edit', user);
        },
        handleDelete(userId) {
            this.$emit('delete', userId);
        },
    },
};
</script>
