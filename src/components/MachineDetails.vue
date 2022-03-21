<template>
  <div
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
          <span class="font-semibold">{{ selectedMachine.location.N }}</span>
        </div>
        <div class="text-left">
          E:
          <span class="font-semibold">{{ selectedMachine.location.E }}</span>
        </div>
        <div class="text-left">
          H:
          <span class="font-semibold">{{ selectedMachine.location.H }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    selectedMachine: {
      required: true,
      type: Object,
    },
  },
  setup() {
    return {};
  },
};
</script>
