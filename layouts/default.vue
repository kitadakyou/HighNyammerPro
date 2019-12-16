<template>
<main class="container">
  <div class="columns">
    <aside id="SidemenuContainer" class="column is-3">
      <b-menu>
        <b-menu-list label="グループ">
            <b-menu-item v-for="group in groups"
                :label=group.name
                tag="router-link"
                :to=group.to>
            </b-menu-item>
        </b-menu-list>
      </b-menu>
    </aside>
      <nuxt />
  </div>
</main>
</template>

<script>
export default {
  data() {
    return  {
      groups: [
        {
          name: "トピック",
          to: "/group/1",
        },
        {
          name: "シフト活動記録",
          to: "/group/2",
        }

      ],
    }
  },
}
</script>

<style scoped>
  #SidemenuContainer {
    text-align: right;
    background: #f5f5f5;
    padding-top: 2rem;
    padding-left: 2rem;
  }
</style>