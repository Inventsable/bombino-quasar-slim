<template>
  <q-pull-to-refresh style="height: 100%;" @refresh="refresh">
    <q-page>
      <div>
        <quasar-logo id="logo" />
      </div>
    </q-page>
  </q-pull-to-refresh>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  components: {
    "quasar-logo": require("src/assets/quasarLogo.vue").default
  },
  data: () => ({}),
  computed: {
    ...mapGetters("settings", ["settings"]),
    app() {
      return this.$root.$children[0];
    },
    size() {
      return this.settings.size;
    }
  },
  async mounted() {
    // await this.app.runCS("init()");
  },
  methods: {
    ...mapActions("settings", ["setSize"]),
    refresh(done) {
      console.log("Refreshing action");
      setTimeout(() => {
        done();
      }, 2000);
    }
  }
};
</script>

<style>
.main-page {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
}
</style>
