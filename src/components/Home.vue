<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume
                :label="'Ahorro total'"
                :total-amount="100000"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts"/>
                </template>
                <template #action>
                    <Action></Action>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
            />
        </template>
    </Layout>
</template>

<script>
import Layout from './Layout.vue';
import Header from './Header.vue';
import Resume from './Resume/Index.vue';
import Action from './Action.vue';
import Movements from './Movements/Index.vue';
import Graphic from './Resume/Graphic.vue';

export default {
    components: {
        Layout,
        Header,
        Resume,
        Action,
        Movements,
        Graphic
    },
    data() {
        return {
            amount: null,
            label: null,
            amounts: [100, 200, -600, 300, -1500, 700, -650],
                movements: [{
                    id: 0,
                    title: "Movimiento 1",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("01-01-2023"),
                },{
                    id: 1,
                    title: "Movimiento 2",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("01-01-2023"),
                },{
                    id: 2,
                    title: "Movimiento 3",
                    description: "Aprende algo dinero.",
                    amount: -1000,
                    time: new Date("02-01-2023"),
                },{
                    id: 3,
                    title: "Movimiento 4",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("02-01-2023"),
                },{
                    id: 4,
                    title: "Movimiento 5",
                    description: "Aprende algo dinero.",
                    amount: -1000,
                    time: new Date("03-01-2023"),
                },{
                    id: 5,
                    title: "Movimiento 6",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("03-01-2023"),
                },{
                    id: 6,
                    title: "Movimiento 7",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("04-01-2023"),
                },{
                    id: 7,
                    title: "Movimiento 8",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("04-01-2023"),
                },{
                    id: 8,
                    title: "Movimiento 9",
                    description: "Aprende algo dinero.",
                    amount: 1000,
                    time: new Date("05-01-2023"),
                },
            ],
        };
    },
    computed:  {
        amounts()  {
            const lastDays = this.movements
            .filter(m => {
                const today = new Date();
                const odlDate = today.setDate(today.getDate() - 30);
                
                return m.time > odlDate;
            })
            .map(m => m.amount)

            return lastDays.map((m, i)=> {
                const lastMovements = lastDays.slice(0, i);

                return lastMovements.reduce((suma, movement) => {
                    return suma + movement
                }, 0);
            });
        }
    }
};

</script>