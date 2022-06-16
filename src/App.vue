<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <div class="tab-container-box">
      Ez egy olyan megoldás, ahol csak a tab konténert használom és azon belül
      definiálom a tab komponenseket, annak átadom a tablistát, ami tartalmazza
      a komponens nevét és címét, meg egy egyedi kulcsot, amivel azonosítani
      lehet.
      <only-tabs-solution />
    </div>

    <div class="tab-container-box">
      Ez viszont egy olyan megoldás, ahol a tab konténer és a tab komponensek
      külön vannak definiálva. Két féle képpen detektálom az aktív tabot.
      <br />
      Az egyik, amikor a tab komponensen meghívok egy click eseményt, amire a
      szülő komponensben fel lehet iratkozni.
      <br />
      Vagy a másik, amikor a tab konténernek használom a boostrap-es eseményét
      és azt tovább osztom a saját tab konténer komponensnek.
      <tabs-and-tab-solution />
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import OnlyTabsSolution from "./components/OnlyTabsSolution.vue";
import TabsAndTabSolution from "./components/TabsAndTabSolution.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    OnlyTabsSolution,
    TabsAndTabSolution,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 90%;
  margin: auto;
  margin-top: 60px;
}
.tab-container-box {
  margin: 40px 0px;
}
</style>
