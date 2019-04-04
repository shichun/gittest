<template>
  <div class="setting_right">
    <ul class="weizhi">
      <p class="weizhi_title">
        {{$t('current_job_position')}}：
      </p>
      <li><a href="/equipment/showEquipmentManageAction.action">Setting </a>
        <p>&gt;</p>
      </li>
      <li><a href="/code/showCodeManageAction.action">Code List</a>
        <p>&gt;</p>
      </li>
      <li><a href="javascript:void(0);">Edit Code</a></li>
    </ul>
    <ul class="add_form">
      <form id="mainform" name="mainform" method="POST">
        <input type="hidden" id="codekey" name="updCodeDto.codekey" />
        <li>
          <p>
            {{$t('code_type')}}:
          </p>
          <span>
            <p align="left" style="margin-left: 20px;">
              <s:if test='updCodeDto.codetype == "PROCESS_TYPE"'>
                Process Type
              </s:if>
              <s:elseif test='updCodeDto.codetype == "UNIT_TYPE"'>
                Unit Type
              </s:elseif>
              <s:elseif test='updCodeDto.codetype == "PARTS_TYPE"'>
                Parts Type
              </s:elseif>
              <s:else>
                <s:property value="updCodeDto.codetype" />
              </s:else>
            </p>
          </span>
        </li>
        <li>
          <p>
            {{$t('code_value')}}:
          </p>
          <span>
            <input type="text" name="updCodeDto.valcn" id="valcn" cssClass="width150" maxlength="64" theme="simple" />
          </span>
        </li>
        <li>
          <p>
            {{$t('code_order')}}:
          </p>
          <span>
            <input type="text" name="updCodeDto.sort" id="sort" cssClass="width150" maxlength="4" theme="simple" />
          </span>
        </li>
        <li>
          <p>
            {{$t('status')}}:
          </p>
          <span>
            <select name="updCodeDto.status" id="status" class="width150">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <s:if test="updCodeDto.status == 1">
                <option value="1" selected="selected">
                  {{$t('valid')}}
                </option>
                <option value="0">
                  {{$t('invalid')}}
                </option>
              </s:if>
              <s:elseif test="updCodeDto.status == 0">
                <option value="1">
                  {{$t('valid')}}
                </option>
                <option value="0" selected="selected">
                  {{$t('invalid')}}
                </option>
              </s:elseif>
              <s:else>
                <option value="1">
                  {{$t('valid')}}
                </option>
                <option value="0">
                  {{$t('invalid')}}
                </option>
              </s:else>
            </select>
          </span>
        </li>
      </form>
    </ul>
    <div class="twobutton">
      <span class="setting_cancel"><a href="/code/showCodeManageAction.action">Cancel </a> </span>
      <span class="setting_save"><a href="javascript:void(0);" onclick="updcode();">Save</a></span></div>
    <div class="clear"></div>
  </div>
</template>
<script>
export default {
  name: "code"
};
</script>
