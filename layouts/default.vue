<template>
<div class="app">
    <b-navbar
      type=""
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
                  <b-dropdown
                    hoverable              
                    v-model="navigation"
                    position="is-bottom-left"
                    aria-role="menu">
                    <a
                        class="navbar-item"
                        slot="trigger"
                        role="button">
                        <span>Menu</span>
                        <b-icon icon="menu-down"></b-icon>
                    </a>

                    <b-dropdown-item custom aria-role="menuitem">
                      <a href="/users/edit" class="user-info">
                        <img :src=user.icon><span class="user-name">{{user.name}}</span>
                      </a>
                    </b-dropdown-item>
                    <hr class="dropdown-divider">
                    <b-dropdown-item has-link aria-role="menuitem">
                        <a href="/analytics/community">
                            <b-icon icon="chart-line"></b-icon>
                            共同体全体の分析
                        </a>
                    </b-dropdown-item>
                    <b-dropdown-item has-link aria-role="menuitem" v-if="user.is_admin">
                        <a href="#">
                            <b-icon icon="settings"></b-icon>
                            管理機能
                        </a>
                    </b-dropdown-item>
                    <b-dropdown-item has-link aria-role="menuitem">
                        <a href="developer/portal">
                            <b-icon icon="pickaxe"></b-icon>
                            開発者機能
                        </a>
                    </b-dropdown-item>
                    <b-dropdown-item has-link aria-role="menuitem">
                        <a href="feed">
                            <b-icon icon="rss"></b-icon>
                            RSSフィード
                        </a>
                    </b-dropdown-item>
                    <b-dropdown-item has-link aria-role="menuitem">
                        <a href="/users/sign_out">
                            <b-icon icon="logout"></b-icon>
                            ログアウト
                        </a>
                    </b-dropdown-item>
                </b-dropdown>
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
