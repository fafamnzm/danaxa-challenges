<template>
  <!-- <v-container>
      <v-row>
      </v-row>
    </v-container> -->
  <div>
    <v-row>
      <v-col cols="4">
        <v-spacer></v-spacer>
      </v-col>
      <v-col cols="4">
        <v-card :dark="theme" align="center" justify="center">
          <v-card-title align="center" justify="center" class="mx-auto">
            <v-row class="mx-auto mt-5" v-for="type in types" :key="type.id">
              <v-checkbox
                v-model="type.value"
                :append-icon="type.icon"
                @click="updateList(type.title)"
              ></v-checkbox>
            </v-row>
          </v-card-title>

          <div v-for="sel in selected" :key="sel.id">
            <v-card-text :append-icon="sel.icon">
              {{ sel.title }} <v-icon>{{ sel.icon }}</v-icon>
            </v-card-text>
          </div>
          <v-card-actions>
            <v-checkbox v-model="theme" label="Change the theme"></v-checkbox>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="4">
        <v-spacer></v-spacer>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "checkbox",
  data: () => ({
    theme: false,
    types: [
      {
        id: 1,
        title: "box_corners",
        value: false,
        icon: "mdi-graph-outline"
      },
      {
        id: 2,
        title: "bounding_box",
        value: false,
        icon: "mdi-shape-square-plus"
      },
      { id: 3, title: "human", value: false, icon: "mdi-human" }
    ],
    subItems: [
      { id: 1, title: "box_corners", value: false, icon: "mdi-graph-outline" },
      { id: 2, title: "box_corners", value: false, icon: "mdi-graph-outline" },
      { id: 3, title: "box_corners", value: false, icon: "mdi-graph-outline" },
      {
        id: 4,
        title: "bounding_box",
        value: false,
        icon: "mdi-shape-square-plus"
      },
      {
        id: 5,
        title: "bounding_box",
        value: false,
        icon: "mdi-shape-square-plus"
      },
      { id: 6, title: "human", value: false, icon: "mdi-human" }
    ]
  }),
  computed: {
    // this.selected = this.subItems.filter(item => item.value === true)
    selected: function() {
      const selectedProp = this.subItems.filter(item => item.value === true)
      console.log(selectedProp)
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

<style></style>
