<template>
  <div width="500" justify="center">
    <v-row>
      <v-col cols="3">
        <v-spacer></v-spacer>
      </v-col>
      <v-col cols="6">
        <v-card :dark="theme">
          <v-card-title class="mx-auto">
            <v-row
              v-for="type in types"
              :key="type.id"
              wdith="500"
              justify="center"
            >
              <v-checkbox
                v-model="type.value"
                color="info"
                @click="updateList(type.title)"
              ></v-checkbox>
              <v-icon style="white">{{ type.icon }}</v-icon>
            </v-row>
          </v-card-title>
          <v-divider></v-divider>
          <v-card-text>
            <v-row v-for="sel in selected" :key="sel.id">
              <v-col cols="3">
                <v-icon :style="{ color: sel.iconcolor }">{{
                  sel.icon
                }}</v-icon>
              </v-col>
              <v-col cols="6">
                {{ sel.title }}
              </v-col>
            </v-row>
          </v-card-text>
          <v-card-actions>
            <v-checkbox v-model="theme" label="Change the theme"></v-checkbox>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="3">
        <v-spacer></v-spacer>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "checkbox",
  data: () => ({
    theme: true, //sets the dark theme
    types: [
      {
        id: 1,
        title: "box_corners",
        value: true,
        icon: "mdi-graph-outline"
      },
      {
        id: 2,
        title: "bounding_box",
        value: true,
        icon: "mdi-shape-square-plus"
      },
      { id: 3, title: "human", value: true, icon: "mdi-human" }
    ],
    subItems: [
      {
        id: 1,
        title: "box_corners",
        value: true,
        icon: "mdi-graph-outline",
        iconcolor: "yellow"
      },
      {
        id: 2,
        title: "box_corners",
        value: true,
        icon: "mdi-graph-outline",
        iconcolor: "green"
      },
      {
        id: 3,
        title: "box_corners",
        value: true,
        icon: "mdi-graph-outline",
        iconcolor: "blueviolet"
      },
      {
        id: 4,
        title: "bounding_box",
        value: true,
        icon: "mdi-shape-square-plus",
        iconcolor: "limegreen"
      },
      {
        id: 5,
        title: "bounding_box",
        value: true,
        icon: "mdi-shape-square-plus",
        iconcolor: "goldenrod"
      },
      {
        id: 6,
        title: "human",
        value: true,
        icon: "mdi-human",
        iconcolor: "teal"
      }
    ]
  }),
  computed: {
    selected: function() {
      const selectedProp = this.subItems.filter(item => item.value === true)
      return selectedProp
    }
  },
  methods: {
    updateList(type) {
      this.subItems.map(item => {
        item.title === type ? (item.value = !item.value) : item
      })
    }
  }
}
</script>

<style scoped>
.v-card_title {
  padding: 0 !important;
}
</style>
