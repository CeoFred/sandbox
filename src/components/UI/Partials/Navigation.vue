<template>
   <div class="navigation_home">
          <div class="nav_logo">
        <img src='../../../assets/images/logo.png' class="App-logo" alt="logo" />
         Sandbox
        </div>

          <div class="user_data" @click="navClicked">
          <img src='../../../assets/images/user.png'/>
           <small v-if="isAuthenticated">
            Hi, {{ user.displayName }}!
          </small>
            <small v-else>Guest</small>
            
          </div>
         
        </div>
</template>
<script>
export default {
  methods: {
    navClicked(){
      this.$emit('initAuth')
    },
    redirectToCodemarkaLogin(){
      if(!this.isAuthenticated)   window.location.href = `https://codemarka.dev/auth/signin?redir=${window.location.origin}`
    },
  },
    computed: {
    user(){
      return this.$store.getters['auth/getUserData'];
    },
    isAuthenticated(){
      return this.$store.getters['auth/authenticated']
    },
  },
}
</script>

<style scoped>
.navigation_home {
  min-height: 9.9%;
    display: flex;
    width: 100%;
    justify-content: space-between;
    color: #fff;
    position: relative;
    align-items: center;
    border-bottom: 1px solid;
}


.nav_logo {
      display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: absolute;
    left: 14px;
    top:9px;
    font-family: 'Barlow Condensed';
}

.nav_logo img.App-logo {
  width:30px;
}
.navigation_home div.user_data {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    padding-right: 10px;
    cursor: pointer;
    align-items: center;
    position: absolute;
    right: 11px;
    top:11px; 
}

.navigation_home img {
      height: 2.4rem;
    width: 2.4rem;
}
</style>