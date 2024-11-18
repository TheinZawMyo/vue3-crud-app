<template>
    <div class="list-group-item d-flex justify-content-between align-items-center">
        <div>
            <h5>{{ user.name }}</h5>
            <p class="mb-0">{{ user.email }}</p>
        </div>
        <div>
            <button class="btn btn-sm btn-warning me-2" @click="$emit('edit', user)">
                Edit
            </button>
            <button class="btn btn-sm btn-danger" @click="$emit('delete', user.id)">
                Delete
            </button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        user: Object,
    },
};
</script>
