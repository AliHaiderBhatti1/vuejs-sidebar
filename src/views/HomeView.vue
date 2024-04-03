<template>
  <div class="d-flex justify-center align-center">
    <sidebar :array="array" />
  </div>
</template>

<script>
import Sidebar from "../components/Sidebar";

export default {
  name: "HomeView",

  components: {
    Sidebar,
  },

  data() {
    return {
      array: [
        {
          id: 1,
          title: "Immobilienlexikon",
          description: "Den Wert Ihres Hauses schätzen lassen.",
          logo: require("../assets/city.svg"),
          selectedLogo: require("../assets/city-selected.svg"),
          chipText: "KI",
          isDropdown: false,
        },
        {
          id: 2,
          title: "Preisschätzung",
          description: "Den Wert Ihres Hauses schätzen lassen.",
          logo: require("../assets/elevator.svg"),
          selectedLogo: require("../assets/elevator-selected.svg"),
          chipText: "LINK",
          isDropdown: false,
        },
        {
          id: 3,
          title: "Checklisten",
          description: "Praktische Checklisten für jeden Schritt.",
          logo: require("../assets/clipboard-check.svg"),
          selectedLogo: require("../assets/clipboard-check-selected.svg"),
          chipText: "PDF",
          isDropdown: true,
          itemsArray: ["Dummy 1", "Dummy 2", "Dummy 3", "Dummy 4", "Dummy 5"],
        },
        {
          id: 4,
          title: "Ratgeber",
          description: "Immobilien-Expertenrat für Eigentümer.",
          logo: require("../assets/ecology-book.svg"),
          selectedLogo: require("../assets/ecology-book-selected.svg"),
          chipText: "PDF",
          isDropdown: true,
          itemsArray: ["Dummy 1", "Dummy 2", "Dummy 3", "Dummy 4", "Dummy 5"],
        },
        {
          id: 5,
          title: "Mandatsnavigator",
          description: "Verständlich zum Verkaufsabschluss.",
          logo: require("../assets/compass.svg"),
          selectedLogo: require("../assets/compass-selected.svg"),
          chipText: "KI",
          isDropdown: false,
        },
        {
          id: 6,
          title: "Wohntraumfinder",
          description: "Zum Traumheim mit KI-Unterstützung.",
          logo: require("../assets/golf.svg"),
          selectedLogo: require("../assets/golf-selected.svg"),
          chipText: "KI",
          isDropdown: false,
        },
      ],
    };
  },
};
</script>
