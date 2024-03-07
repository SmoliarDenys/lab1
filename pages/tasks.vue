<template>
    <div class="container-fluid">
        
        <h4>Tasks</h4>

        <div class="row tasks d-flex justify-content-between">

            <div class="tasks__todo col-3 p-0">
                <div class="tasks__title">ToDo</div>
                <div class="tasks__task">Task #2 20.03</div>
                <div class="tasks__task">Task #2 20.03</div>
                <div class="tasks__task">Task #2 20.03</div>
                <button>+ Add task</button>
            </div>

            <div class="tasks__inProcess col-3 p-0">
                <div class="tasks__title">In process</div>
                <div class="tasks__task">Task #2 20.03</div>
                <button>+ Add task</button>
            </div>

            <div class="tasks__done col-3 p-0">
                <div class="tasks__title">Done</div>
                <div class="tasks__task">Task #2 20.03</div>
                <button>+ Add task</button>
            </div>

        </div>

    </div>
</template>

<style lang="scss" scoped>
    .tasks {
        margin: 0;

        &__todo, &__inProcess, &__done {
            border: 2px solid gray;
            display: flex;
            flex-direction: column;

            button {
                margin-top: auto;
                background: none;
                border: none;
                text-align: start;
                padding: 0 10px 10px 10px;
            }
        }

        &__title {
            border-bottom: 2px solid gray;
            text-align: center;
            padding: 5px;
            margin-bottom: 10px; 
        }

        &__task {
            padding: 5px;
            margin: 0 10px 10px 10px;
            border: 2px solid gray;
            border-radius: 10px;
        }
    }
</style>