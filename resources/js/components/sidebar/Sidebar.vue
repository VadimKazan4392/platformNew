<template>
    <!-- Left sidebar START -->
    <div class="col-xl-3">
        <!-- Responsive offcanvas body START -->
        <div class="offcanvas-xl offcanvas-end" tabindex="-1" id="offcanvasSidebar" aria-labelledby="offcanvasSidebarLabel">
            <!-- Offcanvas header -->
            <div class="offcanvas-header bg-light">
                <h5 class="offcanvas-title" id="offcanvasNavbarLabel">My profile</h5>
                <button  type="button" class="btn-close" data-bs-dismiss="offcanvas" data-bs-target="#offcanvasSidebar" aria-label="Close"></button>
            </div>
            <!-- Offcanvas body -->
            <div class="offcanvas-body p-3 p-xl-0">
                <div class="bg-dark border rounded-3 pb-0 p-3 w-100">
                    <!-- Dashboard menu -->
                    <div class="list-group list-group-dark list-group-borderless">
                        <a class="list-group-item active" href="student-dashboard.html"><i class="bi bi-ui-checks-grid fa-fw me-2"></i>Dashboard</a>
                        <a class="list-group-item" href="student-subscription.html"><i class="bi bi-card-checklist fa-fw me-2"></i>My Subscriptions</a>
                        <a class="list-group-item" href="student-course-list.html"><i class="bi bi-basket fa-fw me-2"></i>My Courses</a>
                        <a class="list-group-item" href="student-course-resume.html"><i class="far fa-fw fa-file-alt me-2"></i>Course Resume</a>
                        <a class="list-group-item" href="student-quiz.html"><i class="bi bi-question-diamond fa-fw me-2"></i>Quiz</a>
                        <a class="list-group-item" href="student-payment-info.html"><i class="bi bi-credit-card-2-front fa-fw me-2"></i>Payment info</a>
                        <a class="list-group-item" href="student-bookmark.html"><i class="bi bi-cart-check fa-fw me-2"></i>Wishlist</a>
                        <a class="list-group-item" href="instructor-edit-profile.html"><i class="bi bi-pencil-square fa-fw me-2"></i>Edit Profile</a>
                        <a class="list-group-item" href="instructor-setting.html"><i class="bi bi-gear fa-fw me-2"></i>Settings</a>
                        <a class="list-group-item" href="instructor-delete-account.html"><i class="bi bi-trash fa-fw me-2"></i>Delete Profile</a>
                        <a class="list-group-item text-danger bg-danger-soft-hover" href="#"><i class="fas fa-sign-out-alt fa-fw me-2"></i>Sign Out</a>
                    </div>
                </div>
            </div>
        </div>
        <!-- Responsive offcanvas body END -->
    </div>
    <!-- Left sidebar END -->
</template>

<script>
export default {
    name: "Sidebar",
    data(){
        return {
            token: null
        }
    },
    methods:{
        getToken(){
            this.token = localStorage.getItem('x_xsrf_token')
        },
        logout(){
            axios.post('/logout')
                .then(res => {
                    localStorage.removeItem('x_xsrf_token')
                    this.$router.go(0);
                    this.$router.push('/login')
                });
        }
    },
    mounted() {
        this.getToken();
    }
}
</script>

<style scoped>

</style>
