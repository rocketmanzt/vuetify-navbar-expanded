<template>
<v-app-bar app dense height="auto" class="py-2"
    v-click-outside="() =>{ 
        if(navbarExpanded) navbarExpanded = !navbarExpanded
    }"
>
    <v-row no-gutters class="align-center">
    <v-col>
        <v-toolbar-title>
         vuetify-expanded navbar
        </v-toolbar-title>
    </v-col>
    <v-spacer></v-spacer>
    <v-col class="hidden-sm-and-down">
        <v-toolbar-items class="d-inline-flex">
        <v-btn text v-for="link in links" :key="link.name">
            {{link.name}}
        </v-btn>
        </v-toolbar-items>
    </v-col>
    <v-btn icon class="hidden-md-and-up" @click="navbarExpanded = !navbarExpanded">
        <v-icon small>fa fa-{{navbarExpanded?'times':'bars'}}</v-icon>
    </v-btn>
    <v-expand-transition>
    <v-col cols="12" class="hidden-md-and-up" v-if="navbarExpanded">
        <v-btn block depressed x-large v-for="link in links" :key="link.name" class="my-4">
        {{link.name}}
        </v-btn>
    </v-col>
    </v-expand-transition>
    </v-row>
</v-app-bar>
</template>


<script>
export default {
  name: 'navbar-app',
  data: () => ({
    links: [
      { name: 'home' },
      { name: 'blog' },
      { name: 'about us' },
      { name: 'contact' },
    ],
    navbarExpanded: false
  })
}
</script>
