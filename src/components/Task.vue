<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3><span :class="{'checked' : isChecked}">{{task.text}}</span>
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <p><span :class="{'checked' : isChecked}">🗓 {{task.day}}</span>
            <i @click="checkTask" class="fas fa-check"></i>
        </p>
        <p><span :class="{'checked' : isChecked}">⏰ {{task.time}}</span>
        </p>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    data(){
        return {
            isChecked: false,
        }
    },
    methods: {
        checkTask(){
            this.isChecked = !this.isChecked;
        }
    }
}
</script>

<style scoped>
h3 .fas {
    color: red; 
}
p .fas {
    color: green; 
}
.task {
    background: #dddcdc;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task.reminder {
    border-left: 5px solid green;
}
.task h3, .task p {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.checked {
    text-decoration: red line-through;
    opacity: 0.5;

}


</style>