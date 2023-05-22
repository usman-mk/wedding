<template>
    <div class="col-3">
        <div class="card bg-light mb-3 shadow">
            <a href="#" class="d-block h-100">
            <!-- <img class="img-fluid img-thumbnail" src="https://source.unsplash.com/aob0ukAYfuI/400x300" alt=""> -->
            <img :src="post.node.thumbnail_src" class="card-img-top" alt="...">
            </a>

            <div class="card-body p-0">
                <div class="row ml-0 mr-0">
                    <div class="col-md-6 border p-2 text-center">
                        <span class="text-muted">
                            <font-awesome-icon icon="heart"/>
                            {{ post.node.edge_media_preview_like.count }}
                        </span>
                    </div>
                    <div class="col-md-6 border p-2 text-center">
                        <span class="text-muted">
                            <font-awesome-icon icon="comment"/>
                            {{ post.node.edge_media_to_comment.count }}
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        post: Object
    }
}
</script>
