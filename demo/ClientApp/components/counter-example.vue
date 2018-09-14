<template>
  <div>
    <h1>Counter</h1>

    <p>This is a simple example of a Vue.js component & Vuex</p>

    <p>
      Current count (Vuex): <strong>{{ currentCount }}</strong>
    </p>
    <p>
      Auto count: <strong>{{ autoCount }}</strong>
    </p>

    <button @click="incrementCounter()">Increment</button>
    <button @click="resetCounter()">Reset</button>
    <br>
    <br>
        <button class="button is-medium is-danger" @click="confirmCustomDelete">
            Delete account
        </button>
    <br>
    <br>

       <section>
        <b-field>
            <b-input placeholder="Search..."
                type="search"
                icon="magnify">
            </b-input>
            <p class="control">
                <button class="button is-primary">Search</button>
            </p>
        </b-field>

        <b-field>
            <b-input placeholder="This is expanded" expanded></b-input>
            <p class="control">
                <span class="button is-static">@gmail.com</span>
            </p>
        </b-field>

        <hr>

        <b-field>
            <b-select placeholder="Currency">
                <option>$</option>
                <option>£</option>
                <option>€</option>
            </b-select>
            <b-input type="number" placeholder="0,00"></b-input>
            <p class="control">
                <button class="button is-success">Transfer</button>
            </p>
        </b-field>

        <b-field>
            <p class="control">
                <button class="button">
                    <b-icon icon="format-bold"></b-icon>
                </button>
            </p>
            <p class="control">
                <button class="button">
                    <b-icon icon="format-italic"></b-icon>
                </button>
            </p>
            <p class="control">
                <button class="button">
                    <b-icon icon="format-underline"></b-icon>
                </button>
            </p>
            <p class="control">
                <button class="button">
                    <b-icon icon="format-align-left"></b-icon>
                </button>
            </p>
            <p class="control">
                <button class="button">
                    <b-icon icon="format-align-center"></b-icon>
                </button>
            </p>
            <p class="control">
                <button class="button">
                    <b-icon icon="format-align-right"></b-icon>
                </button>
            </p>
            <b-input placeholder="Search..." type="search" icon="magnify"></b-input>
        </b-field>

        <b-field>
            <p class="control">
                <button class="button is-primary">
                    Button
                </button>
            </p>
            <p class="control">
                <b-dropdown>
                    <button class="button is-primary" slot="trigger">
                        <b-icon icon="menu-down"></b-icon>
                    </button>

                    <b-dropdown-item>Action</b-dropdown-item>
                    <b-dropdown-item>Another action</b-dropdown-item>
                    <b-dropdown-item>Something else</b-dropdown-item>
                </b-dropdown>
            </p>
        </b-field>

        <b-field>
            <p class="control">
                <b-dropdown>
                    <button class="button" slot="trigger">
                        <span>Filters</span>
                        <b-icon icon="menu-down"></b-icon>
                    </button>

                    <b-dropdown-item value="open_issues">Open Issues and Pull Requests</b-dropdown-item>
                    <b-dropdown-item value="your_issues">Your Issues</b-dropdown-item>
                    <b-dropdown-item value="pull_requests">Your Pull Requests</b-dropdown-item>
                    <b-dropdown-item value="everything">Everything</b-dropdown-item>
                </b-dropdown>
            </p>
            <b-input icon="magnify" type="search" placeholder="Search..."></b-input>
        </b-field>
    </section>
    <br>
      <section>
     
        <table class="table isBordered isStriped isNarrowed isHoverable ">
            <tbody>
              <tr>
                  <td>
                    <b-field label="Name">
                      <b-input v-model="name"></b-input>
                  </b-field>
                  </td>
                  <td>
                    <b-field label="Email"
                      type="is-danger"
                      message="This email is invalid">
                      <b-input type="email"
                          value="john@"
                          maxlength="30">
                      </b-input>
                  </b-field>
                  </td>
              </tr>
                <tr>
                  <td>
                    <b-field label="Username"
                        type="is-success"
                        message="This username is available">
                        <b-input value="johnsilver" maxlength="30"></b-input>
                    </b-field>
                  </td>
                  <td>
                    <b-field label="Password">
                        <b-input type="password"
                            value="iwantmytreasure"
                            password-reveal>
                        </b-input>
                    </b-field>
                  </td>
              </tr>
              
            </tbody>
        </table>
        

        <b-field label="Message">
            <b-input maxlength="200" type="textarea"></b-input>
        </b-field>
    </section>
  </div>

</template>

<script>
  import { mapActions, mapState } from 'vuex'

  export default {
  data() {
  return {
  autoCount: 0,
  name: 'Wandy',
  }
  },

  computed: {
  ...mapState({
  currentCount: state => state.counter
  })
  },

  methods: {
  ...mapActions(['setCounter']),

  incrementCounter: function() {
  var counter = this.currentCount + 1;
  this.setCounter({counter: counter});
  },
  resetCounter: function() {
  this.setCounter({counter: 0});
  this.autoCount = 0;
  },
   confirmCustomDelete() {
                this.$dialog.confirm({
                    title: 'Deleting account',
                    message: 'Are you sure you want to <b>delete</b> your account? This action cannot be undone.',
                    confirmText: 'Delete Account',
                    type: 'is-danger',
                    hasIcon: true,
                    onConfirm: () => this.$toast.open('Account deleted!')
                })
            },
  },

  created() {
  setInterval(() => {
  this.autoCount += 1
  }, 1000)
  }
  }
</script>

<style>
</style>