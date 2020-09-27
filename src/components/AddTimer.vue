.<template>
    <div class="add-timer" @click="$emit('add-new-timer')">
        <i class="fa fa-plus" aria-hidden="true"></i>
    </div>
</template>

<style>
.add-timer{
    width: 225px;
    height: 120px;
    display: flex;
    justify-content: center;
    align-items: center;    
    margin: 25px;
    background: #696969;
    cursor: pointer;
}
.fa-plus {
    color: #9E9E9E;
    font-size: 20px;
}
</style>