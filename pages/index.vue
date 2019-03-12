<template>
  <section class="container">
    <div>
      <Logo/>

      <div class="subcontainer">
        <Button
          ppText="GitHub"
          ppPrimaryColor="#3B8070"
          ppSecondaryColor="white"
          :ppClickFunction="fnRedirect.bind(this, 'https://www.github.com/nuxt/nuxt.js')"
          :ppDisabled="dtDisabled"
        />
        <Button ppText="Toggle" ppPrimaryColor="#35495E" :ppClickFunction="fnToggle"/>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from "~/components/Logo";
import Button from "~/components/Button";

export default {
  components: {
    Logo,
    Button
  },
  data: function() {
    return {
      dtDisabled: true
    };
  },
  methods: {
    fnRedirect: function(link) {
      window.open(link);
    },
    fnToggle: function() {
      this.dtDisabled = !this.dtDisabled;
    }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.subcontainer {
  padding: 5vh;
}
</style>