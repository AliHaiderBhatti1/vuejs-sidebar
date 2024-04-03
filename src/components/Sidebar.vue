<template>
  <div>
    <v-card class="my-6" width="310px">
      <div class="d-flex justify-space-between mt-6">
        <v-icon class="mx-2" @click="isOpen = !isOpen">mdi-menu</v-icon>
        <div class="d-flex">
          <img class="mt-1 mx-2 stars" src="../assets/stars.svg" />
          <v-chip class="mr-4 chip-color">NACHTMODUS</v-chip>
        </div>
      </div>
      <v-expand-transition>
        <div v-if="isOpen">
          <div class="d-flex justify-center mt-2">
            <img src="../assets/immo-logo.svg" />
          </div>
          <div v-if="array" class="mt-6">
            <div
              v-for="item in array"
              :key="item.id"
              class="py-3 px-4 cursor-pointer selected-card"
              :class="selectedItem === item.id ? 'bg-selected' : 'bg-white'"
              @click="selectItem(item.id)"
            >
              <div class="d-flex justify-space-between">
                <img
                  class="logo mt-1"
                  :src="
                    selectedItem === item.id ? item.selectedLogo : item.logo
                  "
                />
                <span
                  class="title"
                  :class="
                    selectedItem === item.id ? 'white--text' : 'selected-text'
                  "
                  >{{ item.title }}</span
                >
                <v-chip
                  class="chip-color mt-1"
                  style="height: 22px"
                  @click.stop="item.isDropdown && selectChip(item.id)"
                  ><span class="mx-2 custom-chip"> {{ item.chipText }} </span>
                  <v-icon v-if="item.isDropdown" class="ml-1" size="18">{{
                    selectedChip === item.id
                      ? "mdi-chevron-up"
                      : "mdi-chevron-down"
                  }}</v-icon>
                </v-chip>
              </div>
              <div
                class="d-flex justify-center mt-2 body-2"
                :class="
                  selectedItem === item.id ? 'white--text' : 'selected-text'
                "
              >
                {{ item.description }}
              </div>
              <v-expand-transition>
                <div v-if="selectedChip === item.id">
                  <div
                    class="d-flex justify-center white--text"
                    v-for="(option, index) in item?.itemsArray"
                    :key="index"
                  >
                    {{ option }}
                  </div>
                </div>
              </v-expand-transition>
            </div>
          </div>
        </div>
      </v-expand-transition>

      <div class="d-flex justify-center pb-2">
        <img src="../assets/Credits.svg" />
      </div>
    </v-card>
  </div>
</template>
<script>
export default {
  name: "SideBar",

  props: ["array"],

  data() {
    return {
      selectedItem: 1, // Represents the selected item
      selectedChip: null, // Represents the selected chip
      isOpen: true, // Indicates if something is open
    };
  },

  methods: {
    /**
     * Selects a sidebar item and deselects the currently selected sidebar item or chip, if any.
     * @param {number} id - The ID of the sidebar item to select.
     */
    selectItem(id) {
      if (this.selectedItem !== id) this.selectedChip = null;
      this.selectedItem = id;
    },

    /**
     * Selects a sidebar chip and deselects the currently selected sidebar item, if any.
     * @param {number} id - The ID of the sidebar chip to select.
     */
    selectChip(id) {
      if (this.selectedChip === id) this.selectedChip = null;
      else {
        this.selectedChip = id;
        this.selectedItem = id;
      }
    },
  },
};
</script>
<style scoped>
.chip-color {
  color: #003f52;
  background-color: #effbff !important;
}
.bg-white {
  background-color: white;
}
.bg-selected {
  background-color: #459e97 !important;
}
.cursor-pointer {
  cursor: pointer;
}
.selected-text {
  color: #00404e !important;
}

.stars {
  width: 24px;
  height: 19px;
}

.custom-chip {
  font-size: 9px;
  font-weight: 700;
}

.selected-card {
  width: 310px;
  min-height: 80px;
}

.logo {
  width: 19px;
  height: 19px;
}

.title {
  font-size: 18px;
  font-weight: 500;
}

.portrait-section {
  position: relative;
  /* Other styles for the portrait section */

  /* Set a background image or color */
  background: url("../assets/city.svg") center/cover; /* Replace 'carlos-kuk-portrait.jpg' with your actual image URL */
}

.gradient-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100px; /* Adjust the height of the gradient overlay as needed */
  background: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 1),
    rgba(255, 255, 255, 0)
  );
}
.fade-transition {
  transition: opacity 0.5s;
}
</style>
