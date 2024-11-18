<template>
    <div class="mt-4">
        <form @submit.prevent="handleSubmit">
            <div class="mb-3">
                <label class="form-label">Name</label>
                <input type="text" v-model="formData.name" class="form-control" required />
            </div>
            <div class="mb-3">
                <label class="form-label">Email</label>
                <input type="email" v-model="formData.email" class="form-control" required />
            </div>
            <button type="submit" class="btn btn-primary me-2">
                {{ editUser ? 'Update' : 'Add' }} User
            </button>
            <button v-if="editUser" type="button" class="btn btn-secondary" @click="cancelEdit">
                Cancel
            </button>
        </form>
    </div>
</template>

<script>
export default {
    props: {
        editUser: Object,
    },
    data() {
        return {
            formData: { name: '', email: '' },
        };
    },
    watch: {
        editUser: {
            immediate: true,
            handler(newVal) {
                this.formData = newVal ? { ...newVal } : { name: '', email: '' };
            },
        },
    },
    methods: {
        handleSubmit() {
            if (this.editUser) {
                this.$emit('update-user', this.formData);
            } else {
                this.$emit('add-user', this.formData);
            }
            this.formData = { name: '', email: '' };
        },
        cancelEdit() {
            this.$emit('update-user', null);
        },
    },
};
</script>
