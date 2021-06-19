<template>
    <div class="row">
        <div class="col-md-4">
            <div style="width: 18rem;">
                <img class="img-avatar" :src="user.avatar_url"  />
                <h3>
                    {{ user.name }} 
                    <p class="user-login">
                        {{ user.login }}
                    </p>
                </h3>
                <ul>
                     <li>
                        <img src="../assets/organization.svg" style="width: 1rem" />
                        <span>{{ user.company }}</span>
                    </li>
                    <li>
                        <img src="../assets/location.svg" style="width: 1rem"  />
                        <span>{{ user.location }}</span>
                    </li>
                    <li>
                        <img src="../assets/star.svg" style="width: 1rem"  />
                        <span>{{ user.public_gists }}</span>
                    </li>
                    <li>
                        <img src="../assets/repository.svg" style="width: 1rem"  />
                        <span>{{ user.public_repos }}</span>
                    </li>
                    <li>
                        <img src="../assets/followers.svg" style="width: 1rem" />
                        <span>{{  user.followers }}</span>
                    </li>
                </ul>
                <div style="margin-top: 15px">
                    <a :href="user.html_url" class="btn btn-dark">Ver mais</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    props: ["user"]
};

</script>

<style>
 .img-avatar{
     width: 200px;
     height: 200px;
 }
 .user-login{
     color: grey; 
     font-size: 1.2rem; 
     font-weight: normal
 }
 ul{
     list-style: none;
 }
 ul li{
     margin-bottom: 10px;
 }
 ul li span{
     color: grey;
     margin-left: 10px
 }
</style>
