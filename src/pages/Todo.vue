<template>
  <q-page class="bg-grey-3 column">
    <q-list separator bordered>
      <q-item
        @click="task.done = !task.done"
        clickable
        :class="{ 'done bg-green-2': task.done }"
        v-for="(task, index) in tasks"
        :key="task.title"
        tag="label"
        v-ripple
      >
        <q-item-section avatar>
          <q-checkbox
            class="no-pointers-events"
            v-model="task.done"
            val="orange"
            color="primary"
          />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn
            @click.stop="deleteTask(index)"
            dense
            flat
            round
            color="primary"
            icon="remove_circle_outline"
          />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {
          title: "hello",
          done: true,
        },
        {
          title: "hello2",
          done: false,
        },
        {
          title: "hello3",
          done: false,
        },
      ],
    };
  },
  methods:{
    deleteTask(index){
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style lang="scss">
.done {
  .q-item__label {
    text-decoration: line-through;
    color: grey;
  }
}
</style>
