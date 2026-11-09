<template>
    <div class="page">
        <h2>Thêm liên hệ mới</h2>
        <ContactForm :contact="{}" @submit:contact="submitContact" />
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactForm,
    },
    methods: {
        async submitContact(data) {
            try {
                await ContactService.create(data);
                alert("Liên hệ được thêm thành công.");
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                alert("Có lỗi xảy ra khi thêm liên hệ.");
            }
        },
    },
};
</script>
