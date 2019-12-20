<template>
<div class="app">
    <b-navbar
      type="is-dark"
      wrapper-class="container"
    >
      <template slot="brand">
          <b-navbar-item tag="router-link" :to="{ path: '/' }">
              HighNyammer Pro
          </b-navbar-item>
      </template>

      <template slot="start">
        <b-navbar-item tag="div">
          媒介中心性: {{ betweeness }}
        </b-navbar-item>
      </template>

      <template slot="end">
          <b-navbar-item tag="div">
              <div class="buttons">
                  <b-field label="">
                    <b-input
                      v-model="searchKeyword"
                      placeholder="キーワードで全文検索"
                      size="is-small"
                      custom-class="seach-bar">
                    </b-input>
                  </b-field>
                  <b-navbar-dropdown label="Menu">
                    <b-navbar-item href="/users/edit">
                      <img :src=user.icon><span class="user-name">{{user.name}}</span>
                    </b-navbar-item>
                    <hr class="dropdown-divider">
                    <b-navbar-item href="/analytics/community">
                        <b-icon icon="chart-line"></b-icon>
                        共同体全体の分析
                    </b-navbar-item>
                    <b-navbar-item v-if="user.is_admin" href="#">
                        <b-icon icon="settings"></b-icon>
                        管理機能
                    </b-navbar-item>
                    <b-navbar-item href="developer/portal">
                        <b-icon icon="pickaxe"></b-icon>
                        開発者機能
                    </b-navbar-item>
                    <b-navbar-item href="feed">
                        <b-icon icon="rss"></b-icon>
                        RSSフィード
                    </b-navbar-item>
                    <b-navbar-item href="/users/sign_out">
                        <b-icon icon="logout"></b-icon>
                        ログアウト
                    </b-navbar-item>
                </b-navbar-dropdown>
              </div>
          </b-navbar-item>
      </template>
    </b-navbar>
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
</div>
</template>

<script>
export default {
  data() {
    return  {
      searchKeyword: '',
      betweeness: 'なし',
      user: {
        name: '江藤光',
        icon: "https://avatars3.githubusercontent.com/u/4303909?s=32&v=4",
        is_admin: false,
      },
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
  #app {
    font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", "ヒラギノ角ゴ ProN W3", Hiragino Kaku Gothic ProN, Arial, "メイリオ", Meiryo, sans-serif;
  }

  #SidemenuContainer {
    text-align: right;
    background: #f5f5f5;
    padding-top: 2rem;
    padding-left: 2rem;
  }

  span.user-name {
    margin-left: .3rem;
    /* ↓正しいやり方を調査 */
    vertical-align: super;
    color: #4a4a4a;
  }

</style>
