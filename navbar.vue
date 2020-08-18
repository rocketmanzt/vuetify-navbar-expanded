<template>
<v-app-bar app dense height="auto" class="py-2"
    v-click-outside="() =>{ 
        if(navbarExpanded) navbarExpanded = !navbarExpanded
    }"
>
    <v-row noGutters class="align-center">
    <v-col>
        <v-toolbar-title style="font-family: 'Baloo Tamma 2'">
        Travel Agency
        </v-toolbar-title>
    </v-col>
    <v-spacer></v-spacer>
    <v-col cols="8" class="hidden-sm-and-down">
        <v-toolbar-items class="d-inline-flex">
        <v-btn text v-for="link in links" :key="link.name">
            {{link.name}}
        </v-btn>
        </v-toolbar-items>
        |
        <v-tooltip v-for="icon in icons" :key="icon.name" bottom>
        <template v-slot:activator="{ attrs, on}">
            <v-btn icon rounded v-on="on" v-bind="attrs">
                <v-icon small>
                    // 
                    fa fa-{{icon.name}} 
                </v-icon>
            </v-btn>
        </template>
        <span>{{icon.name}}</span>
        </v-tooltip>
    </v-col>
    <v-btn icon class="hidden-md-and-up" @click="navbarExpanded = !navbarExpanded">
        <v-icon small>fa fa-{{navbarExpanded?'times':'bars'}}</v-icon>
    </v-btn>
    <v-expand-transition>
    <v-col cols="12" class="hidden-md-and-up" v-if="navbarExpanded">
        <v-btn block depressed x-large v-for="link in links" :key="link.name" class="my-4">
        {{link.name}}
        </v-btn>
        <div class="mt4 d-flex justify-center ">
        <v-btn icon v-for="icon in icons" :key="icon">
            <v-icon>fa fa-{{icon.name}}</v-icon>
        </v-btn>
        </div>
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
      { name: 'explore' },
      { name: 'tours' },
      { name: 'about us' },
      { name: 'contact' },
    ],
    icons: [
      { name: 'facebook' },
      { name: 'instagram' },
      { name: 'twitter' },
      { name: 'linkedin' },
    ],
    cards : [
      { name: 'nature', link: 'nature.jpg'},
      { name: 'travel', link: 'travel.jpg'},
      { name: 'beach', link: 'beach.jpg'},
    ],
    navbarExpanded: false
  })
}
</script>
