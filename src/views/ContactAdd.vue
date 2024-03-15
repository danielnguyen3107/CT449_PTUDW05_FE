<template>
  <div class="page">
    <h4>Thêm mới Liên hệ</h4>
    <ContactForm :contact="contact" @submit:contact="addContact" />
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
      contact: {
        // Khởi tạo một đối tượng rỗng để lưu trữ thông tin mới của liên hệ
        name: "",
        email: "",
        address: "",
        phone: "",
        // Bổ sung các trường dữ liệu khác nếu cần thiết
      },
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      try {
        // Gọi API để tạo liên hệ mới
        await ContactService.create(data);
        // Xác nhận thành công và cập nhật tin nhắn
        this.message = "Liên hệ được thêm thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
