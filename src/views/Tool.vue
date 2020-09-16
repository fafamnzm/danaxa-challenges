<template>
  <div wdith="500" justify="center">
    <v-row>
      <v-col cols="3">
        <v-spacer></v-spacer>
      </v-col>
      <v-col cols="2">
        <v-card dark>
          <v-card-text
            dense
            justify="start"
            v-for="tool in toolSet"
            :key="tool.id"
          >
            <v-radio-group v-model="chosenTool" column>
              <v-radio :value="tool" append-icon="mdi-graph-outline">
                <template v-slot:label>
                  <v-icon>{{ tool.icon }}</v-icon>
                </template>
              </v-radio>
            </v-radio-group>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="4">
        <v-card dense>
          <v-card-title>
            Chosen Tool :
            <div v-if="chosenTool">
              {{ chosenTool.name }} - <v-icon>{{ chosenTool.icon }}</v-icon>
            </div>
            <div v-else>
              Nothing is selected yet!
            </div>
          </v-card-title>
          <!-- <v-card-text
            dense
            justify="start"
            v-for="tool in toolSet"
            :key="tool.id"
          >
            <v-radio-group v-model="chosenTool" column>
              <v-radio :value="tool" append-icon="mdi-graph-outline">
                <template v-slot:label>
                  <v-icon>{{ tool.icon }}</v-icon>
                </template>
              </v-radio>
            </v-radio-group>
          </v-card-text>
          <v-card-actions> </v-card-actions> -->
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
  name: "Tool",
  created() {
    window.addEventListener("keydown", e => {
      if (e.key == "Escape") {
        this.chosenTool = this.toolSet[0]
      }
      if (e.key == "1") {
        this.chosenTool = this.toolSet[1]
      }
      if (e.key == "2") {
        this.chosenTool = this.toolSet[2]
      }
      if (e.key == "3") {
        this.chosenTool = this.toolSet[3]
      }
    })
  },
  mounted: function() {
    this.chosenTool = this.toolSet[0]
  },
  data: () => ({
    toolSet: [
      {
        id: 1,
        name: "Hand",
        shortKey: "Esc",
        icon: "mdi-cursor-pointer"
      },
      {
        id: 2,
        name: "Brush",
        shortKey: "1",
        icon: "mdi-fountain-pen"
      },
      {
        id: 3,
        name: "Pen",
        shortKey: "2",
        icon: "mdi-grease-pencil"
      },
      {
        id: 4,
        name: "Magic wand",
        shortKey: "2",
        icon: "mdi-auto-fix"
      }
    ],
    chosenTool: {}
  })
}
</script>

<style></style>
