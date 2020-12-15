<template>
  <div id="app-body">
    <div id="all-items" class="items-container" v-bind:style="marginLeft">
      <div id="all-items-container">
        <span class="no-items-message">No Items</span>
      </div>
    </div>

    <div id="active-items" class="items-container">
      <div id="active-items-container">
        <span class="no-items-message">No Items</span>
      </div>
    </div>

    <div id="completed-items" class="items-container">
      <div id="completed-items-container">
        <span class="no-items-message">No Items</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Body",
  props: ["tab"],
  computed: {
     marginLeft: function() {
         return "margin-left: " + -(this.tab - 1) * 100 + "%";
     } 
  }
};
</script>

<style scoped>
#app-body {
  flex-grow: 1;
  overflow: hidden;
  display: flex;
}

.todo-item {
  padding: 22px 4px;
  margin: 0px 12px;
  cursor: pointer;
  border-top: 1px solid #e8e8e8;

  display: flex;
  align-items: center;
}

.todo-item.completed .data {
  text-decoration: line-through;
}

.todo-item .data {
  text-decoration: none;
}

.todo-item-content {
  flex-grow: 1;
  color: #7b7b7b;
  padding: 0 16px;
}

.todo-item-date {
  display: flex;
  flex-direction: column;
  text-align: center;
  font-weight: bold;
  background: #ecb2c3;
  padding: 6px 14px;
  border-radius: 6px;
  color: white;
}

.todo-item-date .day {
  font-size: 22px;
}

.todo-item-date .month {
  font-size: 14px;
}

.todo-item:hover .todo-item-content {
  color: #4e4e4e;
}

.delete-btn {
  display: inline-block;
  width: 26px;
  height: 26px;
  background-image: url(../assets/icon-delete-light.png);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;

  flex-shrink: 0;
}

.delete-btn:hover {
  background-image: url(~@/assets/icon-delete.png);
}

::-webkit-scrollbar {
  width: 5px;
}

::-webkit-scrollbar-track-piece {
  background-color: #fff;
}

::-webkit-scrollbar-thumb {
  background-color: #c7c7c7;
}

::-webkit-scrollbar-thumb:hover {
  background-color: #909090;
}

.items-container {
  width: 100%;
  flex-shrink: 0;

  display: flex;
  flex-direction: column;

  overflow: auto;
}

.items-container .no-items-message {
  display: none;
  margin: auto;
}

.no-items-message:only-child {
  display: block;
}

#all-items-container,
#active-items-container,
#completed-items-container {
  display: flex;
  flex-direction: column;
  height: 100%;
}
</style>
