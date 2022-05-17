<template>
  <div class="new-note">
    <label>Title</label>
    <input v-model="note.title" type="text">
    <fieldset class="new-note-priority new-note__priority">
      <label class="new-note-priority__col" v-for="(difficult, idx) in priorities" :key="`priority-${idx}`">
        <input
            type="radio"
            name="notePriority"
            :value="difficult.name"
            class="new-note-priority__input"
            v-model="note.difficult"
        />
        {{ difficult.name }}
      </label>
    </fieldset>
    <label>Description</label>
    <textarea v-model="note.descr"></textarea>
    <button class="btn btnPrimary" @click="addNote">New note</button>
  </div>
</template>

<script>
export default {
  name:  "NewNote",
  props: {
    note: {
      type:     Object,
      required: true,
    }
  },
  data() {
    return {
      priorities: [
        {
          name: 'standard',
        },
        {
          name: 'medium',
        },
        {
          name: 'hard',
        },
      ]
    };
  },
  methods: {
    addNote() {
      this.$emit('addNote', this.note);
    },
  },
};
</script>

<style lang="scss" scoped>
.new-note {
  text-align: center;

  &__priority {
    width: 100%;
    margin-bottom: 25px;
  }
}

.new-note-priority {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #eee;
  padding-top: 12px;
  padding-bottom: 16px;

  &__col {
    display: flex;
    align-items: baseline;
    margin-right: 12px;
    margin-bottom: 0;
  }

  &__input {
    margin-right: 12px;
    width: auto;
    margin-bottom: 0;
  }
}

.btn {
  margin-top: 25px;
  margin-bottom: 25px;
}
</style>
