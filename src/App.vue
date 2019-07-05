<template>
  <div id="app">
    <div class="container">
      <form>
        <h3>Reddit OAuth Retriever</h3>
        <div class="row">
          <div class="input-field col s12">
            <input id="reddit__client-id" type="text" class="validate">
            <label for="reddit__client-id">Client ID</label>
          </div>
          <div class="input-field col s12">
            <input id="reddit__client-secret" type="text" class="validate">
            <label for="reddit__client-secret">Client Secret</label>
          </div>
          <div class="input-field col s12">
            <input id="reddit__client-secret" type="text" class="validate">
            <label for="reddit__client-secret">Redirect URI</label>
          </div>
          <div class="input-field col s12">
            <select>
              <option value disabled selected>Choose your option</option>
              <option value="1">Temporary</option>
              <option value="2">Permanent</option>
            </select>
            <label>Duration</label>
          </div>
          <div class="col s12">
            <div id="scope" class="chips chips-initial"></div>
            <div
              class="chip"
              v-for="scopeName in scopeArray"
              :key="'scope-' + scopeName"
              @click="addChip(scopeName)"
            >{{ scopeName }}</div>
          </div>
          {{ chipsInstance }}
          <button
            class="btn waves-effect waves-light"
            type="submit"
            name="action"
          >Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      scopeArray: [
        "identity",
        "edit",
        "flair",
        "history",
        "modconfig",
        "modflair",
        "modlog",
        "modposts",
        "modwiki",
        "mysubreddits",
        "privatemessages",
        "read",
        "report",
        "save",
        "submit",
        "subscribe",
        "vote",
        "wikiedit",
        "wikiread"
      ],
      chipsInstance: "Cool"
    };
  },
  methods: {
    addChip(scopeName) {
      this.chipsInstance.addChip({
        tag: scopeName
      });
    }
  },
  mounted() {
    M.FormSelect.init(document.querySelectorAll("select"), {});
    this.chipsInstance = M.Chips.init(document.querySelector("#scope"), {
      placeholder: "Scope"
    });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
