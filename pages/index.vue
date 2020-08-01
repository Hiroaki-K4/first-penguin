<template>
    <v-flex
      xs12
      sm12
      md12
    >
      <v-col
          v-for="(item, i) in items"
          :key="i"
          cols="12"
        >
          <v-card
            white
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title
                  class="headline"
                  v-text="item.title"
                ></v-card-title>

                <v-card-subtitle v-text="item.summary"></v-card-subtitle>
                <v-card-subtitle v-text="item.summary_ja"></v-card-subtitle>
                <v-btn :href=item.pdf target="_blank">PDF</v-btn>
              </div>
            </div>
          </v-card>
        </v-col>
    </v-flex>
</template>

<script>
export default {
  data() {
    return {
      items: ''
    }
  },
  async asyncData({ $axios }) {
    const url = "https://first-penguin-284413.uc.r.appspot.com/penguin";
    const response = await $axios.$get(url);
    return {
      items: response
    };
  }
};
</script>
