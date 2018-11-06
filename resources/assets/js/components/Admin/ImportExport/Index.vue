<template>
  <div class="animated">
    <b-row>
      <b-col>
        <b-card class="mb-2 trump-card">
          <div class="card-title">
            <div class="caption">
              <h5><i class="fas fa-table"></i> Models</h5>
            </div>
          </div>
          <table class="table trump-table table-hover">
            <thead>
              <tr>
                <th>Name</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
            	<tr>
            		<td>User Table</td>
            		<td>
            		  <b-button size="sm" @click="exportTable(1)" class="mr-1 btn-blue">
						<i class="fas fa-cloud-download-alt"></i> Export To Excel
            		  </b-button>
            		</td>
            	</tr>
	        	<tr>
	        		<td>Role Table</td>
	        		<td>
	        		  <b-button size="sm" @click="exportTable(2)" class="mr-1 btn-blue">
						<i class="fas fa-cloud-download-alt"></i> Export To Excel
	        		  </b-button>
	        		</td>
	        	</tr>
            </tbody>
          </table>
        </b-card>
      </b-col>
    </b-row>
    <!-- Info modal -->
    <b-modal class="ess-modal" id="modalInfo" ref="editModal" hide-footer @hide="resetModal" :title="modalInfo.title">
      <!-- <pre>{{ modalInfo.data }}</pre> -->
      <form @submit.prevent="editRole" :row="modalInfo.row" ref="editRoleForm">
        <input type="hidden" name="id" :value="modalInfo.data.id">
        <div class="form-group">
          <label for="exampleFormControlInput1">Name</label>
          <input type="text" name="name" v-bind:value="modalInfo.data.name" class="form-control" placeholder="" required>
        </div>
        <b-btn class="mt-3 pull-right" variant="primary" type="submit">Update</b-btn>
        <b-btn class="mt-3 pull-right" style="margin-right:5px;" variant="default" @click="hideRoleModal">Cancel</b-btn>
      </form>
    </b-modal>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        loading: true,
        table_items: [],
        role_table_fields: ['name', 'action'],
        modalInfo: {
          title: '',
          content: '',
          data: []
        },
      }
    },
    created() {
    },
    computed: {
      // edit_option_for_parent_role: function (roleOptionId, parentId, roleId) {
      //  console.log(roleOptionId);
      // }
    },
    methods: {
      resetModal() {
        this.modalInfo.title = 'Edit Role'
        this.modalInfo.content = ''
      },
      exportTable: function(type) {
      	let self = this
        let url = self.$root.baseUrl + '/admin/export-table/' + type;

        var win = window.open(url, '_blank');
        win.focus();

        self.$swal({
        // position: 'top-end',
        type: 'success',
        title: 'Exported updated successfully.',
        showConfirmButton: true,
        // timer: 1500,
        customClass: 'crm-swal',
        confirmButtonText: 'Thanks',
      })

      	// axios.post(url, {type: type}).then(function(response) {
       //      if (response.status === 200) {
       //        self.$swal({
       //          // position: 'top-end',
       //          type: 'success',
       //          title: 'Exported updated successfully.',
       //          showConfirmButton: true,
       //          // timer: 1500,
       //          customClass: 'crm-swal',
       //          confirmButtonText: 'Thanks',
       //        })
       //      }
       //    })
       //    .catch(function(error) {});
      },
      showModal() {
        this.$refs.myModalRef.show()
      },
      hideModal() {
        this.$refs.myModalRef.hide()
      },
      hideRoleModal() {
        this.$refs.editModal.hide();
      },
    },
  }
</script>