<template>
  <div class="task" :class="stateClass" @click="$emit('taskStateChanged', task)">
    <span class="close" @click.stop="$emit('taskDeleted', task)">X</span>
    <p>{{task.name}}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending
      };
    }
  }
};
</script>

<style>
.task {
  position: relative;
  box-sizing: border-box;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}

.pending {
  border-left: 12px solid darkred;
  background-color: red;
}

.done {
  color: #ddd;
  border-left: 12px solid rgb(11, 107, 40);
  background-color: green;
  text-decoration: line-through;
}

.pending .close {
  background-color: #b73229;
}

.done .close {
  background-color: rgb(11, 107, 40);
}

.close {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 0.9rem;
  font-weight: 600;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
}
</style>