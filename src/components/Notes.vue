<template>
  <div class="notes">
    <div class="note" :class="{'note--is-full' : !isGrid}" v-for="(note, index) in notes" :key="index">
      <div class="note-header">
        <p>{{ note.title }}</p>
        <p style="cursor: pointer;" @click="removeNote(index)">x</p>
      </div>
      <div class="note-body">
        <p>{{ note.descr }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Notes",
  props: {
    notes: {
      type: Array,
      required: true,
    },
    isGrid: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      this.$emit('removeNote', index);
    },
  },
};
</script>

<style scoped lang="scss">
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
    background-color: #ffffff;
    transition: all .25s cubic-bezier(0.02, 0.01, 0.47, 1);
    box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);

    &:hover {
      box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
      transform: translate(0, -6px);
      transition-delay: 0s;
    }

    &--is-full {
      width: 100%;
      text-align: center;

      .note-header {
        justify-content: center;

        p {
          margin-right: 16px;

          &:last-child {
            margin-right: 0;
          }
        }
      }
    }
  }

  .note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    p {
      color: #402caf;
      font-size: 22px;
    }
  }

  .note-body {
    p {
      margin: 20px 0;
    }

    span {
      font-size: 14px;
      color: #999;
    }
  }
</style>
