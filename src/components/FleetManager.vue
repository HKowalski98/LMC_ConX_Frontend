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
      <div
        v-if="selectedMachine"
        class="flex flex-col w-4/5 ml-auto mr-auto bg-orange-300 rounded-lg justify-start"
      >
        <div class="flex flex-row gap-4 mt-2 ml-4">
          <div class="uppercase ">
            id: <span class="font-semibold">{{ selectedMachine.id }} </span>
          </div>
          <div class="uppercase ">
            type:
            <span class="font-semibold">{{ selectedMachine.type }} </span>
          </div>
          <div class="uppercase">
            make: <span class="font-semibold">{{ selectedMachine.make }} </span>
          </div>
          <div class="uppercase ">
            active:
            <span class="font-semibold">{{ selectedMachine.active }} </span>
          </div>
        </div>
        <div class="uppercase flex flex-col mt-10 w-1/2 ml-4 mb-4">
          <div class="text-left">Location:</div>
          <div>
            <div class="text-left">
              N:
              <span class="font-semibold">{{
                selectedMachine.location.N
              }}</span>
            </div>
            <div class="text-left">
              E:
              <span class="font-semibold">{{
                selectedMachine.location.E
              }}</span>
            </div>
            <div class="text-left">
              H:
              <span class="font-semibold">{{
                selectedMachine.location.H
              }}</span>
            </div>
          </div>
        </div>
      </div>
      <div v-else>No selection</div>
    </div>
  </div>
</template>

<script>
import { computed, ref } from "@vue/runtime-core";
import machines from "../api/mockApi";
export default {
  name: "FleetManager",
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
