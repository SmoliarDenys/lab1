<script setup>
import { ref, onMounted, computed, watch} from 'vue'

const group = ref ('')
const first_name = ref('')
const last_name = ref('')
const gender = ref('')
const birthday = ref('')

const student_edit_id = ref('')

const students = ref([
    {'id': Math.random().toString(16).slice(2), 'group': 'groupName', 'name': 'nameTeasdfast2', 'gender': 'M', 'birthday': '11.03.2004', 'status': 'OK'},
    {'id': Math.random().toString(16).slice(2), 'group': 'groupName2', 'name': 'nameTest2', 'gender': 'M', 'birthday': '11.03s.2004', 'status': 'OK'},
])

const openCreateWindow = () => { document.querySelector('.addStudent_block').style.left = '0' }
const closeCreateWindow = () => { document.querySelector('.addStudent_block').style.left = '-100vw' }
const openEditWindow = eId => { 
    document.querySelector('.editStudent_block').style.left = '0' 
    student_edit_id.value = eId;
}
const closeEditWindow = () => { document.querySelector('.editStudent_block').style.left = '-100vw' }

const createNewStudent = () => {
    students.value.push({
        'id': Math.random().toString(16).slice(2), 
        'group': group.value, 
        'name': first_name.value + ' ' + last_name.value, 
        'gender': gender.value, 
        'birthday': birthday.value, 
        'status': 'OK'
    })

    closeCreateWindow()
}



const editStudent = () => {
    students.value = students.value.map(e => {
        if (e.id == student_edit_id.value) {
            e.group = group.value
            e.name = first_name.value + ' ' + last_name.value
            e.gender = gender.value
            e.birthday = birthday.value
        }
        return e;
    })
}

const deleteStudent = student => {
    students.value = students.value.filter(e => e.name != student) 
}

</script>

<template>
    <div class="container-fluid">
        
        <h4>Students</h4>

        <div class="d-flex justify-content-end">
            <button class="addStudent" @click="openCreateWindow()">+</button>
        </div>

        <div class="addStudent_block d-flex justify-content-center align-items-center">
            <div class="addStudent_block__white">
                
                <div class="d-flex justify-content-between">
                    <h3>Add student</h3> 
                    <button class="addStudent_block__close" @click="closeCreateWindow()">x</button>
                </div>

                <div class="addStudent_block__field d-flex justify-content-between mt-5">
                    <span>Group</span>
                    <select 
                        name="select" 
                        v-model="group"
                    >
                        <option value="value1">gruop1</option>
                        <option value="value2" selected>group2</option>
                        <option value="value3">group3</option>
                    </select>
                </div>
                <div class="addStudent_block__field d-flex justify-content-between"><span>First name</span><input type="text" v-model="first_name"></div>
                <div class="addStudent_block__field d-flex justify-content-between"><span>Last name</span><input type="text" v-model="last_name"></div>
                <div class="addStudent_block__field d-flex justify-content-between">
                    <span>Gender</span>
                    <select name="select" v-model="gender">
                        <option value="value1">M</option>
                        <option value="value2" selected>F</option>
                    </select>
                </div>
                <div class="addStudent_block__field d-flex justify-content-between mb-5"><span>Birthday</span><input type="date" v-model="birthday"></div>
            
                <div class="addStudent_block__save d-flex justify-content-end">
                    <button @click="createNewStudent()">Ok</button>
                    <button @click="createNewStudent()" class="ms-2">Create</button>
                </div>
            </div>
        </div>

        <div class="editStudent_block d-flex justify-content-center align-items-center">
            <div class="editStudent_block__white">
                
                <div class="d-flex justify-content-between">
                    <h3>Edit student</h3> 
                    <button class="editStudent_block__close" @click="closeEditWindow()">x</button>
                </div>

                <div class="editStudent_block__field d-flex justify-content-between mt-5">
                    <span>Group</span>
                    <select 
                        name="select" 
                        v-model="group"
                    >
                        <option value="value1">gruop1</option>
                        <option value="value2" selected>group2</option>
                        <option value="value3">group3</option>
                    </select>
                </div>
                <div class="editStudent_block__field d-flex justify-content-between"><span>First name</span><input type="text" v-model="first_name"></div>
                <div class="editStudent_block__field d-flex justify-content-between"><span>Last name</span><input type="text" v-model="last_name"></div>
                <div class="editStudent_block__field d-flex justify-content-between">
                    <span>Gender</span>
                    <select name="select" v-model="gender">
                        <option value="value1">M</option>
                        <option value="value2" selected>F</option>
                    </select>
                </div>
                <div class="editStudent_block__field d-flex justify-content-between mb-5"><span>Birthday</span><input type="date" v-model="birthday"></div>
            
                <div class="editStudent_block__save d-flex justify-content-end">
                    <button @click="editStudent()">Ok</button>
                    <button @click="editStudent()" class="ms-2">Create</button>
                </div>
            </div>
        </div>

        <table>
            <tr>
                <th>
                    <div class="d-flex justify-content-center align-items-center">
                        <input type="checkbox">
                    </div>
                </th>
                <th>Group</th>
                <th>Name</th>
                <th>Gender</th>
                <th>Birthday</th>
                <th>Status</th>
                <th>Options</th>
            </tr>

            <tr
                v-for="(student, index) in students" 
                :key="index"
            >
                <Student 
                    :id="student.id"
                    :group="student.group" 
                    :name="student.name"
                    :gender="student.gender"
                    :birthday="student.birthday"
                    :status="student.status"
                    :deleteFunc="deleteStudent"
                    :openEdit="openEditWindow"
                />
            </tr>
        </table>

    </div>
</template>

<style lang="scss" scoped>
    .addStudent {
        background: none;
        border: 2px solid gray;
        padding: 5px 10px;
        margin-bottom: 20px;
    }

    .addStudent_block, .editStudent_block {
        background: #0000002c;
        position: fixed;
        left: -100vw;
        top: 0;
        height: 100vh;
        width: 100vw;

        &__white {
            background: white;
            width: 30%;
            padding: 40px 20px;
            border: 3px solid gray;
            border-radius: 20px;
        }

        &__close {
            border: 2px solid gray;
            background: none;
            padding: 10px 20px;
        }

        &__field {
            margin: 10px 0;
            padding: 0 10%;

            input, select {
                padding: 5px 10px;
                outline: none;
                border: 2px solid rgb(172, 172, 172);
                width: 60%;
            }
        }

        &__save {
            button {
                background: none;
                border: 2px solid gray;
                padding: 5px 10px;
            }
        }
    }

    table {
        border: 2px solid rgb(140 140 140);
        width: 100%;

        th,
        td {
            border: 1px solid rgb(160 160 160);
            padding: 20px;
            text-align: center;

            input {
                width: 20px;
                height: 20px;
                padding: 0;
                margin: 0;
                border: none;
            }

            button {
                border: 2px solid gray;
                padding: 5px 10px;
                background: none;
            }
        }
        }
</style>