<template>
    <div class="row">
        <div class="col-md-6">
            <h3><a :href="repo.html_url" target="_blank" class="btn-repositorio"> {{repo.name}} </a><br /></h3>
            <p class="description">Descrição: {{ repo.description }} <br />
                <img src="../assets/star.svg" style="width: 1rem" />
                <span>{{ repo.stargazers_count }}</span><br />
            </p>
        </div>
    </div>
</template>

<script>
export default {
    props: ["repo"]
};
</script>
<style lang="css" scoped>
    .btn-repositorio{
        text-decoration: none;
        color: black;
        font-weight: normal
    }
    .description{
        color: grey;
        text-align: row;
    }
    span{
        color: grey;
        margin-left: 10px
    }
</style>
