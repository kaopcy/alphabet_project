<template>
    <div id="Table">
        <div>
            <form @submit.prevent="handleSubmit">
                <label class="Font001">Enter Word :  </label>
                <input type="text"  v-model="Form.name" class="Font001" placeholder="insert word..">
                <br> 
                <label class="Font001" >Enter Path : </label>
                <input type="text"  v-model="Form.phone" class="Font001" placeholder="insert path.."> 
                <br>
                <button class="button001">Submit</button>
            </form>
        </div>
        <div class="tbl-header">
             <table  cellpadding="0" cellspacing="0" border="0">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Phone</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="people in peopleArray" :key="people.id"  >
                        <td>{{people.name}}</td>
                        <td>{{people.phone}}</td>   
                    </tr>
                </tbody>
            </table>
            <div></div>
        </div>
       

    </div>
  
</template>

<script>
export default {
    name: "Table",
    props:{
    },
    data() {
        return {
            peopleArray:[
                
                
                
            ],
            Form:{
                name:'',
                phone:'',
            }
        }
    },
    methods: {
        handleSubmit(){
            const lastID = this.peopleArray.length;
            const id = lastID + 1;
            const newPeopleArray =  {...this.Form , id};
            this.peopleArray = [...this.peopleArray,newPeopleArray]
            this.Form.name = '',
            this.Form.phone = ''
            
        }
    },

}
</script>

<style>
    :root{
        --font: 18px;
    }
    .Font001{
        padding: 5px;
        margin-bottom: 20px;
        color:chartreuse;
        font-size: var(--font);
        font-weight: 600;
    }
    table{
        width:100%;
        table-layout: fixed;
    }
    .tbl-header{
        background-color: rgba(255,255,255,0.4);
    }
        .tbl-content{
        height:300px;
        overflow-x:auto;
        margin-top: 0px;
        border: 1px solid rgba(255,255,255,0.3);
    }
    th{
        padding: 20px 15px;
        text-align: left;
        font-weight: 500;
        font-size: var(--font);
        color: #fff;
        text-transform: uppercase;
    }
    td{
        padding: 15px;
        text-align: left;
        vertical-align:middle;
        font-weight: 400;
        font-size: var(--font);
        color: white;
        border-bottom: solid 1px rgba(255,255,255,0.1);
    }
    @import url(https://fonts.googleapis.com/css?family=Roboto:400,500,300,700);
    body{
        background: -webkit-linear-gradient(left, #25c481, #25b7c4);
        background: linear-gradient(to right, #25c481, #25b7c4);
        background-image: url('https://encrypted-https://gfycat.com/https://gfycat.com/blackandwhiteenergeticalbacoretuna://thumbs.gfycat.com/FlatDisguisedHake-mobile.mp4.gstatic.com/images?q=tbn:ANd9GcTsTIIh0d12-ITg2_XBslSxpQ8buBRjI1OMEA&usqp=CAU');
        font-family: 'Roboto', sans-serif;
        
    }
    section{
        margin: 50px;
    }
    .button001{
        font-weight: '900';
                color: 'grey';
                font-family: 'Open Sans';
                font-size: '30px';
                margin: '20px';
                padding: '10px';
                padding-right:'30px';
                padding-left:'30px';
                border-radius: '20px';
    }

</style>