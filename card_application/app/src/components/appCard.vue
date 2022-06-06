<template>
    <div>
        <b-card no-body class="overflow-hidden" style="max-width: 540px;">
            <b-row no-gutters>
            <b-col md="6">
                <b-card-img src="https://picsum.photos/400/400/?image=20" alt="Image" class="rounded-0"></b-card-img>
            </b-col>
            <b-col md="6">
                <b-card-body>
                <b-card-text>
                    {{ currentResultList.question }}
                    <br><br><br>
                    {{ currentResultList.correct_answer}}
                </b-card-text>
                </b-card-body>
            </b-col>
            </b-row>
        </b-card>
        <br>
        <b-button :disabled="backButtonTest" @click="previousResultList" variant="outline-primary">Back</b-button>
        <b-button :disabled="nextButtonTest" @click="nextResultList" variant="outline-primary">Next</b-button>
    </div>
</template>

<script>
export default{

    props:
    {
        index: Number,  
        currentResultList: Object,
        nextResultList: Function,
        previousResultList: Function,
    },

    computed:{
        backButtonTest: function(){
            if(this.index == 0)
            {
                return true
            }
            else
            {
                return false
            }
        },

        nextButtonTest: function(){
            return (this.index >= 9) ? true : false
        }
    }
}
</script>

<style>
    div{
        left: 32.5%;
    }

    .btn{
        margin:0 150px;
    }
</style>