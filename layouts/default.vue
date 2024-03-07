<template>
    <div class="DefaultLayout">
        <Navbar/>

        <div class="container">
            <div class="row mt-5">

                <div class="left col-3">
                    <ul>
                        <li><NuxtLink to="/dashboard">Dashboard</NuxtLink></li>
                        <li><NuxtLink to="/students">Students</NuxtLink></li>
                        <li><NuxtLink to="/tasks">Tasks</NuxtLink></li>
                    </ul>
                </div>

                <div class="right col-9">
                    <slot/>
                </div>

            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .left {
        ul {
            padding: 0;
            
            li {
                list-style-type: none;
                margin-bottom: 10px;
            }
        }
    }
</style>