<template>
    <header :class="{'scrolled-nav': scrolledNav }">

    <nav>
        <div class="branding">
             <RouterLink to="/">
            <img src="../img/logo2.png" alt="LaRue Fashion">
             </RouterLink>
        </div>
     
        <ul v-show="!mobile" class="navigation1">
            <RouterLink class="link" to="">Smykker</RouterLink>
            <RouterLink class="link" to="">Design dit smykke</RouterLink>
            <RouterLink class="link" to="">Kontakt os</RouterLink>
            <RouterLink class="link" to="">Om os</RouterLink>
            <button class="link">Workshop</button>
        </ul>
        <div class="icon">
            <i @click="toggleMobileNav" v-show="mobile" class="fa-solid fa-bars" :class="{'icon-active' : moblieNav}"></i>
        </div>
        <transition name="moblie-nav">
         <ul v-show="moblieNav" class="dropdown-nav">
            <RouterLink class="link" to="">Smykker</RouterLink>
            <RouterLink class="link" to="">Design dit smykke</RouterLink>
            <RouterLink class="link" to="">Kontakt os</RouterLink>
            <RouterLink class="link" to="">Om os</RouterLink>
            <button class="link">Workshop</button>
         </ul>
      
        </transition>
    </nav>
    </header>
  </template>
  
  <script>


  export default {
    name: "navigation",
    data() {
        return {
            scrolledNav: null,
            mobile: null,
            moblieNav: null,
            windowWidth: null,
        };
    },
    created() {
        window.addEventListener("resize", this.checkScreen);
        this.checkScreen();
    },
    methods: {
        toggleMobileNav() {
            this.moblieNav = !this.moblieNav;
        },
        updateScroll() {
            const scrollPosition = window.scrollY;
            if (scrollPosition > 50) {
                this.scrolledNav = true;
                return;
            }
            this.scrolledNav = false;
        },
        checkScreen() {
            this.windowWidth = window.innerWidth;
            if (this.windowWidth <= 768) {
                this.mobile = true;
                return;
            }
            this.mobile = false;
            this.moblieNav = false;
            return;
        },
    }
};
  </script>
  
  <style lang="scss" scoped>

 
  header {
    background-color: #fff;
    z-index: 99;
    width: 100%;
    transition: .5s ease all;
    

  nav {
    position: relative;
    display: flex;
    flex-direction: row;
    padding: 10px 0;
    transition: .5s ease all;
    width: 90%;
    margin: 0 auto;
    

    @media (min-width: 1140px) {    
        max-width: 1140px;
    }

    ul, .link {
        color:#333;
        list-style: none;
        text-decoration: none;
    }

    li {
        padding: 5px; //Rykker dem
        margin-left: 2px; // Rykker dem
    }
    .link {
        font-size: 15px; // Størrlsen på skiften i header 
        font-weight: 700;
        transition: .5s ease all;
        margin-right: 40px; // mellemrum mellem hianden

        &:hover {
            color: #F6C1A7; //Farven på teksten når den hovers
        }
    }

    .navigation1 button, .dropdown-nav button {
        padding: 10px 20px 10px;
        border-radius: 5px;
        border-color: #F6C1A7;
        border: 3px solid;
        color: #F6C1A7;
        background-color: #fff;

        &:hover {
            color: #333; //Farven på teksten når den hovers
            background-color: #F6C1A7;
            border-color: #F6C1A7;
        }
    }

    .branding {
       display: flex;
       align-items: center; 

       img {
        width: 150px; //str på icon Larue
       }
    }


    .navigation1 {
        display: flex;
        cursor: pointer;
        align-items: center;
        flex: 1;
        justify-content: right; //Ændre hvor på siden de er. Lige er de 3 i midten af headeren
    }


    .icon{
        display: flex;
        align-items: center;
        position: absolute;
        top: 0;
        right: 20px; //Ændre hvilke side af header den skal være på
        height: 100%; // op eller ned. Lige nu midten
        color: #333;

        i {
            cursor: pointer;
            font-size: 25px; //str på brugermenu
            transition: .8s ease all;
        }
    }

    .icon-active {
        transform: rotate(180deg);
    }

    .dropdown-nav{
        display: flex;
        flex-direction: column;
        position: fixed;
        align-items: center;
        width: 100%;
        max-width: 300px; // hvor bred den skal på til siden
        height: 100%;
        z-index: 99;
        background-color: #fff;
        top: 10; // styre den hvor meget den er på toppen
        left: 0; //Styre den hvilken side den er på

        .link {
            margin-left: 45px;
            margin-top: 20px; //Mellerum mellem dem TLF
                color: #333;
                border-color: #F6C1A7;


        }
    }

    .down {
        display: flex;
        flex-direction: column;
        position: fixed;  
        align-items: center;
        top: 25rem; // styre den hvor meget den er på toppen
        left: 0; //Styre den hvilken side den er på
    }

}
}


    .moblie-nav-enter-active,
    .moblie-nav-leave-active {
        transition: 1s ease all;
    }

    .moblie-nav-enter-from, 
    .moblie-nav-leave-to{
        transform: translateX(-250px);
    }

    .moblie-nav-enter-to {
        transform: translateX(0);
    }


  
  .main-list {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .main-list li {
    margin-right: 20px;
    margin-left: 20px;
    
  }
  
  .main-list li a {
    cursor: pointer;
    color: white;
    font-size: 15px;
    padding: 10px 10px;
  }


  @media (max-width: 768px) {    
    .main-list li {
        margin-right: -30px;
        margin-left: 20px;

  }

  .main-list li a {
    font-size: 10px;
  }

    }

</style>