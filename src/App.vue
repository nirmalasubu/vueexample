<template>
    <div id="app">

        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item active">
                        <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Link</a>
                    </li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            Dropdown
                        </a>
                        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                            <a class="dropdown-item" href="#">Action</a>
                            <a class="dropdown-item" href="#">Another action</a>
                            <div class="dropdown-divider"></div>
                            <a class="dropdown-item" href="#">Something else here</a>
                        </div>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
                    </li>
                </ul>
                <form class="form-inline my-2 my-lg-0">
                    <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
                </form>
            </div>
        </nav>
        <typeahead :options="options" v-model="selected"></typeahead>
        <vue-bootstrap-typeahead :data="options"
                                 v-model="addressSearch"
                                 size="lg"
                                 :serializer="s => s.text"
                                 placeholder="Type an address..."
                                 @hit="selectedAddress = $event">
            <template slot="suggestion" slot-scope="{ data, htmlText }">
                <span v-html="htmlText"></span>&nbsp;
                <small>{{ data.code }}</small>
            </template>
        </vue-bootstrap-typeahead>
    </div>
</template>

<script>
    import Typeahead from './components/HelloWorld'
    import VueBootstrapTypeahead from 'vue-bootstrap-typeahead'
export default {
  name: 'app',
  components: {
      Typeahead,
      VueBootstrapTypeahead
  },
  data() {
    return {
      selected: null,
      options: [
        {id: 1, text: 'Apple'},
        {id: 2, text: 'Mango'},
        {id: 3, text: 'Cherry'},
        {id: 4, text: 'Orange'},
        {id: 21, text: 'Appl22e'},
        {id: 22, text: 'Mang2o'},
        {id: 23, text: 'Cher2ry'},
        {id: 24, text: 'Oran2ge'},
        {id: 41, text: 'A4pple'},
        {id: 42, text: 'Ma4ngo'},
        {id: 43, text: 'Ch4erry'},
        {id: 44, text: 'Ora4nge'}
        ],
        addresses: [],
        addressSearch: '',
        selectedAddress: null
    }
  },

  mounted() {
      this.$nextTick(() => {
          jQuery('.hello').hide();
          jQuery('.hello').fadeIn('slow');
      });
        }
}
</script>

<style>
body {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px auto;
  width: 300px;
}
* {
  box-sizing: border-box;
}
</style>
