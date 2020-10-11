<template>
  <v-card
    class="d-flex flex-column justify-space-around align-center flex-wrap"
  >
    <Description />
    <BigImage />
    <Video />
    <Group />
    <How />
    <ContactForm />
  </v-card>
</template>

<script>
import Description from "@/components/Description.vue";
import BigImage from "@/components/BigImage.vue";
import Video from "@/components/Video.vue";
import Group from "@/components/Group.vue";
import How from "@/components/How.vue";
import ContactForm from "@/components/ContactForm.vue";

export default {
  name: "Home",
  components: {
    Description,
    BigImage,
    Video,
    Group,
    How,
    ContactForm
  }
};
</script>
