<template>
  <div class="sidebar">
    <div class="sb-container">
      <v-card height="100%" dark flat tile class="server-info">
        <v-card height="48" tile class="server-title">
          <div style="line-height:48px">Discord Clone</div>
        </v-card>
        <v-card height="235" class="tips" tile>
          Discord Clone was made with Vue.js & Vuetify
          <br />
          <v-btn color="indigo" class="ma-4">Ayo GG!!</v-btn>
        </v-card>

        <v-card tile class="channels">
          <v-list width="100%" rounded dense>
            <v-subheader>SERVER</v-subheader>
            <v-list-item-group v-model="item" color="primary">
              <v-list-item v-for="(item, i) in items" :key="i">
                <v-list-item-icon>
                  <v-icon v-text="item.icon"></v-icon>
                </v-list-item-icon>
                <v-list-item-content>
                  <v-list-item-title
                    class="channel-title"
                    v-text="item.text"
                  ></v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-item-group>
          </v-list>
        </v-card>
      </v-card>
    </div>

    <v-card
      height="52"
      dark
      tile
      flat
      class="mystats"
      @click="toggleAC"
    >
      <v-list-item class="grow">
        <v-list-item-avatar color="grey darken-3">
          <v-img class="elevation-6" :src="$store.state.myIcon"></v-img>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title>{{ $store.state.myNick }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-card>
  </div>
</template>

<script>
export default {
  components: {},

  data() {
    return {
      item: 0,
      items: [
        { text: "Announcements", icon: "mdi-bell-alert" },
        { text: "Rules", icon: "mdi-file-check" },
        { text: "Welcome", icon: "mdi-emoticon" }
      ]
    };
  },

  updated() {
    this.$store.commit("changeChannel", this.item);
  },

  methods: {
    toggleAC() {
      this.$store.commit("toggleAC");
    }
  },

  mounted() {
    this.$store.commit("updateChannels", this.items);
  }
};
</script>
