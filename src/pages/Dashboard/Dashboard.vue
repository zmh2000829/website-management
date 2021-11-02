<template>
  <v-container fluid>
    <div class="dashboard-page">
      <v-row no-gutters class="d-flex justify-space-between mt-10 mb-6">
        <h1 class="page-title">主页</h1>
      </v-row>
      <v-row>
        <v-col cols="12">
          <v-card class="support-requests mx-1 mb-1">
            <v-card-title class="pa-6 pb-0">
              <p>返校申请统计</p>
              <v-spacer></v-spacer>
              <v-menu>
                <template v-slot:activator="{ on, attrs }">
                  <v-btn icon v-bind="attrs" v-on="on">
                    <v-icon color="textColor">mdi-dots-vertical</v-icon>
                  </v-btn>
                </template>
                <v-list>
                  <v-list-item
                    v-for="(item, i) in mock.menu"
                    :key="i"
                    @click="() => {}"
                  >
                    <v-list-item-title>{{ item }}</v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-menu>
            </v-card-title>
            <v-card-text class="pa-0">
              <v-data-table
                :headers="mock.headers"
                :items="mock.table"
                class="elevation-1"
              >
                <template v-slot:[`item.pics`]="{ item }">
                  <div>
                    <v-row>
                      <v-col cols="3" v-for="(pic, i) in item.pics" :key="i">
                        <v-img 
                          :src="pic" 
                          @click="viewImage(pic)" 
                          class="showImg"
                          max-width="300"></v-img>
                      </v-col>
                    </v-row>
                  </div>
                </template> 
                <template v-slot:[`item.action`]>
                  <div style="display: flex;flex-direction: column;">
                    <v-btn
                      class="text-capitalize"
                      small
                      color="primary"
                      @click="login"
                    >
                    允许
                    </v-btn>
                    <br>
                    <v-btn
                      class="text-capitalize"
                      small
                      color="error"
                      @click="login"
                    >
                    拒绝
                    </v-btn>
                  </div>
                </template> 
              </v-data-table>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
import mock from "./mock";

export default {
  name: "Dashboard",
  components: {
    
  },
  data() {
    return {
      mock
    };
  },
  methods: {
    viewImage(url) {
      console.log(123)
      window.open(url)
    }
  },
  mounted() {

  },
};
</script>

<style src="./Dashboard.scss" lang="scss"/>
