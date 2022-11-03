<template>
    <div v-if="contact" class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="addContact"/>
    </div>
</template>

<script>
import ContactService from "../services/contact.service";
import ContactForm from "../components/ContactForm.vue";

export default {
    components: { ContactForm },
    data() {
        return {
            contact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: false,
            },
        };
    },
    methods: {
        async addContact(data) {
            try {
                const result = await ContactService.create(data);
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>