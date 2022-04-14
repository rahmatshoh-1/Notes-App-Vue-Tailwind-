<template>
  <div class="notes">
    <div
      class="note"
      :class="{ full: !grid }"
      v-for="(note, index) in notes"
      :key="index"
    >
      <div class="note_header">
        <p>{{ note.title }}</p>
        <p class="cursor-pointer" @click="removeNote(index)">x</p>
      </div>
      <div class="note_body">
        <p>{{ note.desc }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    notes: {
      type: Array,
      required: true,
    },
    grid: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      console.log(`Note id -${index} removed`);
      this.$emit("remove", index);
    },
  },
};
</script>
<style>
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}
.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #fff;
  transition: all 500ms;
  box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);
}
.note:hover {
  transform: translate(0, -6px);
  transition-delay: 0ms;
  box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
}
.note.full {
  justify-content: center;
  width: 100%;
}
.note_header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.note_header p {
  font-size: 22px;
  color: #54eb9c;
}
.note_body p {
  margin: 20px 0;
}
.note_body span {
  font-size: 14px;
  color: #999;
}
svg {
  margin-right: 12px;
  color: #999;
  cursor: pointer;
}
svg.active {
  color: #54eb9c;
}
svg:last-child {
  margin-right: 0;
}
</style>
