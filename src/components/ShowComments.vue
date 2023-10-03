<script setup>
import { ref } from 'vue';
import TopComments from './TopComments.vue';

    const props = defineProps(['comment'])
    // console.log(props.comment.comments);
    const isExists = ref(false) ;
    
    function checkLength() {
        if(Object.keys(props.comment).includes('comments')){
            isExists.value = props.comment.comments.length > 0 ? true : false ;
        }
        // return isExists ;
    }
    checkLength() ;

    const more = ref(true) ;

    const url = ref('https://ui-avatars.com/api/?name=' + props.comment.auther.split(' ').at(0).charAt(0) 
    + props.comment.auther.split(' ').at(1).charAt(0)) 

    const showReplies = ref(false) ;
    
</script>

<template>
    <div>
        <div v-if="!(comment.picture).endsWith('32x32')">
            <img :src="comment.picture" class="virat-images"/>
        </div>
        <div>
            <ul>
                <li>
                    <div class="auther-image">
                        <img class="avatar" :src='url' alt="">
                        <h4>{{ comment.auther }}</h4>
                    </div>
                    <ul>
                        <li>
                            <span v-if="more">
                                {{ comment.comment.substring(0,100) }} 
                                <span class="view" @click="more = !more">view more</span> 
                            </span>
                            <span v-else>
                                {{ comment.comment }}
                                <span class="view" @click="more = !more">view less</span> 
                            </span>
                            <p @click="showReplies = !showReplies" v-if="isExists">
                                {{ showReplies ? 'Hide Replies' : 'Show Replies' }}
                            </p>
                            <!-- <p v-else>Hide Replies</p> -->

                            <!-- <ShowComments v-if="isExists" :comment="comment.comments"/> -->
                            <template v-if="isExists">
                                <TopComments :array="comment.comments" v-show="showReplies"/>
                            </template>
                        </li>
                    </ul>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
    li {
        list-style: none;
    }
    h4 {
        margin:0
    }
    span .view {
        cursor: pointer;
        font-style: italic;
    }
    .avatar {
        width: 30px;
        border-radius: 100%;
    }
    .auther-image {
        display: flex;
        gap: 0.5rem;
        align-items: center;
    }
    p {
        cursor: pointer;
    }
    .virat-images {
        border-radius: 20px;
        width: 100%;
    }
</style>