<template>
  <div class="fleet-manager flex flex-row mt-10">
    <div class="flex flex-col gap-y-4 w-1/2   ">
      <div v-for="(machine, index) in machinesList" :key="machine.id">
        <div
          class="w-4/5 ml-auto mr-auto  flex flex-col bg-green-200 mb-10 rounded-md cursor-pointer py-2"
          @click="handleMachineClick(machine)"
        >
          <div class="uppercase font-bold">
            {{ index + 1 }}. Type: {{ machine.type }}
          </div>
          <div class="uppercase font-semibold">
            active: {{ machine.active }}
          </div>
        </div>
      </div>
    </div>
    <div class="flex flex-col w-1/2 ">
      <MachineDetails
        v-if="selectedMachine"
        :selectedMachine="selectedMachine"
      ></MachineDetails>
      <div v-else>No selection</div>
    </div>
  </div>
</template>

<script>
import { computed, ref } from "@vue/runtime-core";
import MachineDetails from "./MachineDetails.vue";
import machines from "../api/mockApi";
export default {
  name: "FleetManager",
  components: {
    MachineDetails,
  },
  setup() {
    const machinesList = computed(() => {
      return machines.filter(
        (item) => item.active && item.type === "excavator"
      );
    });
    const selectedMachine = ref(null);

    const handleMachineClick = (machine) => {
      if (selectedMachine.value && selectedMachine.value.id === machine.id) {
        selectedMachine.value = null;
      } else {
        selectedMachine.value = machine;
      }
    };

    return { machinesList, handleMachineClick, selectedMachine };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
