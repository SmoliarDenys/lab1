<template>
    <div class="container-fluid">
        <div class="row">

            <div class="left col-8">
                <div class="graf_btns">
                    <button>Day</button>
                    <button>Month</button>
                </div>
            </div>

            <div class="right col-4">
                <div class="right__informations">
                    <p>Informations</p>
                    <ul>
                        <li>27.02 - Begiinig of studies</li>
                    </ul>
                </div>
                <div class="right__tasks">
                    <p>Tasks</p>
                    <ul>
                        <li>27.02 - Begiinig of studies</li>
                    </ul>
                </div>
                <div class="right__notifications">
                    <p>Notifications</p>
                    <ul>
                        <li>27.02 - Begiinig of studies</li>
                    </ul>
                </div>
            </div>

        </div>
    </div>
</template>

<style lang="scss" scoped>
    .left {
        .graf_btns {
            button { 
                background: none;
                padding: 5px 15px;
                border: 2px solid gray;

                &:first-child {
                    margin-right: 20px;
                }
            }
        }
    }

    .right {
        &__informations, &__tasks, &__notifications {
            border: 2px solid gray;
            padding: 10px 5px;
            margin-bottom: 20px;

            ul {
                padding: 0;

                li {
                   list-style-type: none;
                }
            }
        }
    }
</style>