<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-10">
                <a :href="repo.html_url" :title="repo.description">
                    {{ repo.full_name }}</a>
            </div>
            <div class="col-2">
                <p class="text-end">{{ repo.forks_count }}</p>
            </div>
        </div>
    </div>
</template>

<script>

export default{
    name: 'GitHubRepo',
     props:[
        'repo'
    ]    
}
</script>

<style>

</style>