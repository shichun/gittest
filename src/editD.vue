<template>
  <div class="setting_right">
    <ul class="weizhi">
      <p class="weizhi_title">
        {{$t('current_job_position')}}：
      </p>
      <li><a href="/equipment/showEquipmentManageAction.action">Setting </a>
        <p>&gt;</p>
      </li>
      <li><a href="/department/showDepartmentManageAction.action">Department List</a>
        <p>&gt;</p>
      </li>
      <li><a href="javascript:void(0);">Edit Department</a></li>
    </ul>
    <ul class="add_form">
      <form id="mainform" name="mainform" method="POST">
        <!-- <div style="position:absolute;margin-top:-30px;margin-left:120px; color:red;font-size:14px;font-weight:bold;">
          <s:actionmessage />
        </div> -->
        <li>
          <p>
            {{$t('department_name')}}:
          </p>
          <span>
            <input type="text" name="updDepartmentDto.departname" id="departname" cssClass="width150" maxlength="32" theme="simple" />
          </span>
        </li>
        <li>
          <p>
            {{$t('department_owner')}}:
          </p>
          <span>
            <input type="text" name="updDepartmentDto.departmanager" id="departmanager" cssClass="width150" maxlength="32" theme="simple" />
          </span>
        </li>
        <li>
          <p>
            {{$t('owner_contact')}}:
          </p>
          <span>
            <input type="text" name="updDepartmentDto.phone" id="phone" cssClass="width150" maxlength="32" theme="simple" />
          </span>
        </li>
        <li>
          <p>
            {{$t('status')}}:
          </p>
          <span>
            <select v-model="updDepartmentDto.status" id="status" class="width150">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <option value="1">
                {{$t('valid')}}
              </option>
              <option value="0">
                {{$t('invalid')}}
              </option>
            </select>
          </span>
        </li>
        <li>
          <p>
            {{$t('remarks')}}:
          </p>
          <span>
            <input type="text" name="updDepartmentDto.note" id="note" cssClass="width150" maxlength="128" theme="simple" />
          </span>
        </li>
      </form>
    </ul>
    <div class="twobutton">
      <span class="setting_cancel"><a href="/department/showDepartmentManageAction.action">Cancel </a> </span>
      <span class="setting_save"><a href="javascript:void(0);" onclick="upd();">Save</a></span></div>
    <div class="clear"></div>
  </div>
</template>
