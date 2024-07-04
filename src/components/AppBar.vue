<template>
    <v-app-bar color="#1aa29d" prominent>
      <!-- <v-app-bar-nav-icon icon="mdi-menu" color="#fff" variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon> -->
      <!-- <v-app-bar-nav-icon icon="mdi-checkbox-multiple-blank-outline" color="#fff" variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>  -->
      <!-- <v-toolbar-title  class="ma-0" text="Publisher Platform">
        <v-icon icon="mdi-checkbox-multiple-blank-outline" size="small" class="ma-2" @click.stop="drawer = !drawer"> 
          </v-icon> -->
      <!-- <v-app-bar-nav-icon icon="mdi-menu" color="#fff" variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon> -->
      <!-- </v-toolbar-title>  -->
      <v-btn
    prepend-icon="mdi-checkbox-multiple-blank-outline"
    append-icon="mdi-menu"
    variant="text"
    @click.stop="drawer = !drawer"
  >
  Publisher Platform
  </v-btn>
      <v-col cols="4" >
      <v-text-field
          :loading="false"
          append-inner-icon="mdi-magnify"
          density="compact"
          label="Search"
          variant="outlined"
          hide-details
          single-line
          @click:append-inner="false"
        ></v-text-field>
      </v-col>
      <v-spacer></v-spacer>
      <v-col cols="1" class="">
          <v-btn density="default" icon="mdi-bell-outline"></v-btn>
      </v-col>
      <a class="ma-4">{{ user.fullName }}</a> 
        <v-menu
          class="mr-2"
          min-width="200px"
          rounded
        >
          <template v-slot:activator="{ props }">
            <v-btn
              icon
              v-bind="props"
              class="mr-2"
            >
              <v-avatar
                image=""
                color="#156064"
                size="48"
                
              >
                <span class="text-h6 ma-8">{{ user.initials }}</span>
              </v-avatar>
            </v-btn>
          </template>
          <v-card>
            <v-card-text>
              <div class="mx-auto text-center">
                <v-avatar
                  color="#156064"
                >
                  <span class="text-h6">{{ user.initials }}</span>
                </v-avatar>
                <h3>{{ user.fullName }}</h3>
                <p class="text-caption mt-1">
                  {{ user.email }}
                </p>
                <v-divider class="my-3"></v-divider>
                <v-btn
                  variant="text"
                  rounded
                >
                  Log out
                </v-btn>
              </div>
            </v-card-text>
          </v-card>
        </v-menu>
    </v-app-bar>
    <v-navigation-drawer  v-model="drawer" color="#f6f6f6">
      <v-list
            density="compact"
            nav
            color="#1aa29d"
          >
            <v-list-item nav prepend-icon="mdi-home-outline" title="หน้าแรก" value="first_page"></v-list-item>
            <v-list-item prepend-icon="mdi-newspaper-variant-outline" title="ข่าวทั้งหมด" value="all_news"></v-list-item>
            <v-list-item prepend-icon="mdi-video" title="วิดีโอ" value="video"></v-list-item>
            <v-list-item prepend-icon="mdi-image-outline" title="รูปภาพ" value="image"></v-list-item>
            <v-list-item title="การติดต่อสื่อสาร" class="ma-2" style="color: #1aa29d; "></v-list-item>
            <v-list-item prepend-icon="mdi-bullhorn"  title="ประกาศ" value="post" ></v-list-item>
            <v-list-item prepend-icon="mdi-book-open-outline" title="กระดานสนทนา" value="chat_board"></v-list-item>
            <v-list-item title="รายงาน" class="ma-2" style="color: #1aa29d; font-size: medium;  font-weight: bolder;"></v-list-item>
            <v-list-item prepend-icon="mdi-note-text-outline" title="รายงานสรุปการส่งข่าว" value="report_sent" ></v-list-item>
            <v-list-item prepend-icon="mdi-note-text-outline" title="รายงานสรุปยอดข่าว-ภาพ" value="report_image"></v-list-item>
            <v-list-item prepend-icon="mdi-note-text-outline" title="รายงานสรุปการใช้งานข่าว" value="report_usage" ></v-list-item>
            <v-list-item title="สิทธิการใช้งาน" class="ma-2" style="color: #1aa29d;"></v-list-item>
            <v-list-item prepend-icon="mdi-account" title="Admin" value="admin"></v-list-item>
  
            
      </v-list>    
    </v-navigation-drawer>
  </template>
      
      <script>
      export default {
      setup () {
      
      return {
      }
      },
      data: () => ({
      drawer: null,
      group: null,
      user: {
          initials: 'BT',
          fullName: 'Blishtech',
          email: 'test@one.th',
        },
      }),
      
      methods: {
      },
      
      watch: {
        group () {
          this.drawer = false
        },
      },
      created() {
      },
      computed: {
      }
      }
      </script>
      
      
  <style>
  @import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
  *{
    font-family: "Kanit", sans-serif;
    font-style: normal;
  }
  </style>
    
      