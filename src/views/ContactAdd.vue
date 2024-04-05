<template>
    <div class="page">
        <h4>Thêm liên hệ mới</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="updateContact"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";

    export default {
        components: {
            ContactForm,
        },
        data() {
            return {
                contact: {},
                message: "",
            };
        },
        methods: {
            async updateContact(data){
                try{
                    await ContactService.create(data);
                    this.message = "Liên hệ đã được thêm vào thành công";
                } catch(error){
                    console.log(error);
                }
            },
        },
    }
</script>