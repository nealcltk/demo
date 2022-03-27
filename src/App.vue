<template>
  <div id="app-component" class="container-fluid">
    <navbar alignment="right">
      <template #content>
        <nav-item-text
          v-for="(item, index) in navItems"
          :key="index"
          :link="item"
        ></nav-item-text>
      </template>
    </navbar>
    <div class="row" id="page-content">
      <router-view v-slot="{ Component, route }">
        <transition
          appear
          enter-active-class="animated fadeIn"
          :key="route.path"
        >
          <suspense>
            <template #default>
              <component :is="Component" />
            </template>
            <template #fallback>
              <div>Loading...</div>
            </template>
          </suspense>
        </transition>
      </router-view>
    </div>
  </div>
</template>

<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import NavItemText from "@/components/NavItemText.vue";
import NavItemProps from "@/types/NavItemProps";

const navItems: NavItemProps[] = [
  { href: "/", label: "Home" },
  { href: "/about", label: "About" },
];
</script>

<style lang="scss">
#app-component {
  #page-content {
    padding-top: 84px;
  }
}
</style>
