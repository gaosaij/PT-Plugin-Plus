<template>
  <v-footer app fixed>
    <span class="pl-2 grey--text text--darken-1">
      &copy; 栽培者 2019, 版本 {{version}}
      <v-chip label outline color="orange" disabled small v-if="isDebugMode">{{ words.isDebugMode }}</v-chip>
    </span>
    <v-spacer></v-spacer>
    <v-btn flat small to="/system-logs">系统日志</v-btn>
  </v-footer>
</template>
<script lang="ts">
import { APP } from "../../service/api";
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      words: {
        isDebugMode: APP.debugMode ? "当前处于调试模式" : ""
      },
      version: "",
      isDebugMode: APP.debugMode
    };
  },
  created() {
    if (APP.isExtensionMode) {
      this.version = "v" + chrome.runtime.getManifest().version;
    } else {
      this.version = "localVersion";
    }
  }
});
</script>
