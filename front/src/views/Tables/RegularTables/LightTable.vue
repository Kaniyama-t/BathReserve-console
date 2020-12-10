<template>
    <b-card no-body>
        <b-card-header class="border-0">
            <h3 class="mb-0">User List</h3>
            <b-form class="navbar-search form-inline mr-sm-3"
                :class="{'navbar-search-dark': type === 'default', 'navbar-search-light': type === 'light'}"
                id="table-search-main">
                <br />
                <br />
                <b-input placeholder="Search" class="form-control-alternative"/>
                <base-button icon type="secondary">
                	<v-icon name="search"/>
                </base-button>
            </b-form>
        </b-card-header>

        <el-table class="table-responsive table"
                  header-row-class-name="thead-light"
                  :data="user">
            <el-table-column label="ID"
                             min-width="310px"
                             prop="id">
                <template v-slot="{row}">
                    <b-media no-body class="align-items-center">
                        <a href="#" class="avatar rounded-circle mr-3">
                            <img alt="Image placeholder" src="img/user_avatar.png">
                        </a>
                        <b-media-body>
                            <span class="font-weight-600 name mb-0 text-sm">{{row.id}}</span>
                        </b-media-body>
                    </b-media>
                </template>
            </el-table-column>

            <el-table-column label="Activate"
                             prop="active"
                             min-width="100px">
                <template v-slot="{row}">
                    <i v-if="row.active" class="ni ni-check-bold success"></i>
                    <i v-else class=""></i>
                </template>
            </el-table-column>

            <el-table-column label="Name"
                             prop="name"
                             min-width="180px">
            </el-table-column>

            <el-table-column label="dormitory"
                             min-width="170px"
                             prop="dormitory">
                <template v-slot="{row}">
                    <badge class="badge-dot mr-4" type="">
                        <i :class="`bg-${row.dormitoryCSS}`"></i>
                        <span class="status" :class="`text-${row.dormitoryCSS}`">{{row.dormitoryType}}</span>
                    </badge>
                </template>
            </el-table-column>

            <el-table-column label="Created At"
                             prop="CreatedAt"
                             min-width="140px">
            </el-table-column>

            <!-- <el-table-column label="Users" min-width="190px">
                <div class="avatar-group">
                    <a href="#" class="avatar avatar-sm rounded-circle" data-toggle="tooltip"
                       data-original-title="Ryan Tompson">
                        <img alt="Image placeholder" src="img/theme/team-1.jpg">
                    </a>
                    <a href="#" class="avatar avatar-sm rounded-circle" data-toggle="tooltip"
                       data-original-title="Romina Hadid">
                        <img alt="Image placeholder" src="img/theme/team-2.jpg">
                    </a>
                    <a href="#" class="avatar avatar-sm rounded-circle" data-toggle="tooltip"
                       data-original-title="Alexander Smith">
                        <img alt="Image placeholder" src="img/theme/team-3.jpg">
                    </a>
                    <a href="#" class="avatar avatar-sm rounded-circle" data-toggle="tooltip"
                       data-original-title="Jessica Doe">
                        <img alt="Image placeholder" src="img/theme/team-4.jpg">
                    </a>
                </div>
            </el-table-column> -->

            <!-- <el-table-column label="Completion"
                             prop="completion"
                             min-width="240px">
                <template v-slot="{row}">
                    <div class="d-flex align-items-center">
                        <span class="completion mr-2">{{row.completion}}%</span>
                        <div>
                            <base-progress :type="row.statusType" :value="row.completion"/>
                        </div>
                    </div>
                </template>
            </el-table-column> -->
        </el-table>

        <b-card-footer class="py-4 d-flex justify-content-end">
            <base-pagination v-model="currentPage" :per-page="10" :total="50"></base-pagination>
        </b-card-footer>
    </b-card>
</template>
<script>
  import Vue from 'vue'
  import user from './../user'
  import { Table, TableColumn} from 'element-ui'
  import 'vue-awesome/icons'
  import Icon from 'vue-awesome/components/Icon'
  Vue.component('v-icon', Icon)

  export default {
    name: 'light-table',
    components: {
      [Table.name]: Table,
      [TableColumn.name]: TableColumn
    },
    data() {
      return {
        user,
        currentPage: 1
      };
    }
  }
</script>
