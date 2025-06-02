<template>
  <div class="navbar" :class="{ scrolled: isScrolled }" :style="navbarStyle">
    <div class="navbar-content">
      <a class="tittle-navbar" href="#home" @click.prevent="handleNavClick('home')">KetutTourGuide</a>
      <div class="hamburger-menu" :class="{ open: isMenuOpen }" @click="toggleMenu">
        <span></span>
        <span></span>
        <span></span>
      </div>
      <ul :class="['navigation-list', { active: isMenuOpen }]">
        <li>
            <a href="#home" @click.prevent="handleNavClick('home')">Home</a>
        </li>
        <li>
            <a href="#about" @click.prevent="handleNavClick('about')">About</a>
        </li>
        <li>
            <a href="#services" @click.prevent="handleNavClick('services')">Our Services</a>
        </li>
        <li style="margin-right: 0 !important;">
            <a href="#contact" @click.prevent="handleNavClick('contact')">Contact</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted, computed } from "vue";

export default {
  setup() {
    const isScrolled = ref(false);
    const isMenuOpen = ref(false);
    const isMenuVisible = ref(false);

    const handleScroll = () => {
      isScrolled.value = window.scrollY > 50;
    };

    const scrollTo = (id) => {
      const element = document.getElementById(id);
      if (element) {
        window.scrollTo({
        top: element.offsetTop - 50,
        behavior: "smooth",
        });
      }
    };

    const handleNavClick = (id) => {
      if (id) scrollTo(id);
      closeMenu();
    };

        const toggleMenu = () => {
            if (!isMenuOpen.value) {
                isMenuOpen.value = true;
                isMenuVisible.value = true;
            } else {
                isMenuOpen.value = false;
                setTimeout(() => {
                isMenuVisible.value = false;
                }, 500);
            }
        };

        const closeMenu = () => {
            isMenuOpen.value = false;
            setTimeout(() => {
                isMenuVisible.value = false;
            }, 500);
        };

        const navbarStyle = computed(() => {
            if (isScrolled.value && isMenuOpen.value) {
                return { backdropFilter: "none" };
            } else if (isScrolled.value && !isMenuOpen.value) {
                return { backdropFilter: "blur(10px)" };
            } else {
                return {};
            }
        });

        onMounted(() => {
            window.addEventListener("scroll", handleScroll);
            function setViewportHeight() {
                document.documentElement.style.setProperty(
                "--vh",
                `${window.innerHeight * 0.01}px`
                );
            }
            setViewportHeight();
                window.addEventListener("resize", setViewportHeight);
        });

        onUnmounted(() => {
            window.removeEventListener("scroll", handleScroll);
        });

        return {
            isScrolled,
            isMenuOpen, 
            isMenuVisible,
            toggleMenu,
            closeMenu,
            handleNavClick,
            navbarStyle,
        };
    },
};
</script>

<style scoped>
:root {
  --vh: 1vh;
}
a {
  text-decoration: none;
}
.navbar {
  background-color: transparent;
  position: fixed;
  top: env(safe-area-inset-top, 0);
  left: 0;
  width: 100vw;
  z-index: 99;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  display: flex;
  justify-content: center;
  box-sizing: border-box;
  padding: 20px;
}
.scrolled {
  background-color: #57575744;
  box-shadow: 0px 4px 4px #00000040;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  padding: 10px;
}
.navbar-content {
  display: flex;
  width: 100%;
  max-width: 1200px;
  align-items: center;
  justify-content: space-between;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
.navbar.scrolled .navbar-content {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.tittle-navbar {
  font-size: 1.2em;
  font-family: "Helvetica-Bold", Helvetica;
  font-weight: 700;
  color: #ffffff;
  white-space: nowrap;
}
.navigation-list {
  list-style: none;
  display: flex;
  margin-left: auto;
  padding-left: 0 !important;
}
.navigation-list li {
  margin: 0 2em;
}
.navigation-list .contact {
  margin: 0 0 0 2em;
}
.navigation-list li a {
  font-family: "Helvetica-Regular", Helvetica;
  font-weight: 400;
  color: #ffffff;
  font-size: 1em;
  white-space: nowrap;
  text-decoration: none;
}
.hamburger-menu {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  height: 20px;
  cursor: pointer;
  z-index: 102;
  transition: transform 0.3s ease-in-out;
}
.hamburger-menu span {
  width: 25px;
  height: 3px;
  background-color: #000;
  margin: 2px 0;
  transition: 0.4s;
}
.hamburger-menu.open span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}
.hamburger-menu.open span:nth-child(2) {
  opacity: 0;
}
.hamburger-menu.open span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}
/* Responsive */
@media (max-width: 768px) {
  .navbar {
    max-width: 768px;
    width: 100vw;
    padding: 10px;
  }
  .hamburger-menu {
    display: flex;
  }
  .tittle-navbar {
    z-index: 103;
  }
  .tittle-navbar.active {
    z-index: 100;
  }
  .navbar-content {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    box-sizing: border-box;
  }
  .navigation-list {
    list-style: none;
    display: flex;
    transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;
    transform: translateX(100%);
    z-index: 101;
    flex-direction: column;
    position: absolute;
    top: 0;
    right: 0;
    margin: 0;
    padding: 0;
    width: 42%;
    height: 100vh;
    background-color: #ffffff;
    text-align: left;
    justify-content: center;
  }
  .navlist-bg {
    list-style: none;
    visibility: hidden;
    pointer-events: none;
    transition: opacity 0.5s ease-in-out, visibility 0.5s ease-in-out;
    opacity: 0;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(10px);
    position: fixed;
    z-index: 100;
  }
  .navigation-list.active {
    transform: translateX(0);
    z-index: 101;
    opacity: 1;
  }
  .navlist-bg.active {
    transition: opacity 0.5s ease-in-out, visibility 0.5s ease-in-out;
    visibility: visible;
    pointer-events: auto;
    opacity: 1;
    z-index: 100;
  }
  .navigation-list.open ~ .tittle-navbar {
    opacity: 0;
  }
  .navigation-list li {
    margin: 1em 3em;
  }
  .navigation-list .contact {
    margin: 1em 0;
  }
  .tittle-navbar {
    font-size: 2em;
    transition: opacity 0.3s ease-in-out;
  }
  .navigation-list li a {
    font-size: 1.2em;
  }
}
@media (max-width: 480px) {
  .tittle-navbar {
    font-size: 1.2em;
    color : #000;
  }
  .navigation-list {
    width: 69%;
  }
  .navigation-list li a {
    color: #000 !important;
  }
}
</style>
