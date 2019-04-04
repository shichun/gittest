<template>
  <div class="setting_right">
    <ul class="weizhi">
      <p class="weizhi_title">
        {{$t('current_job_position')}}：
      </p>
      <li><a href="kits/showEquipmentManageAction.action"> Setting </a>
        <p>&gt;</p>
      </li>
      <li><a href="/kits/showKitsManageAction.action">Kits List</a>
        <p>&gt;</p>
      </li>
      <li><a href="javascript:void(0);">Edit Kits</a></li>
    </ul>
    <ul class="add_form">
      <form id="mainform" name="mainform" enctype="multipart/form-data" method="POST">
        <li>
          <p>
            {{$t('kits_id')}}:
          </p>
          <span>
            <p align="left" style="margin-left: -60px;">
              {{updKitsDto.kitssn}}
            </p>
          </span>
        </li>
        <li>
          <p>
            {{$t('equipment_type')}}:
          </p>
          <span>
            <select class="width150" v-model="updKitsDto.equipmenttype" id="equipmenttype" onchange="selectEquipType(this);">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <option v-for="item in equipmentBomList" :key="item.id" :value="item.id">{{item.nodename}}
              </option>
            </select>
          </span>
        </li>
        <li>
          <p>
            {{$t('kits_type')}}:
          </p>
          <span>
            <select class=" width150" v-model="updKitsDto.kitstype" id="kitstype" onchange="selectKitsType(this);">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <option v-for="item in kitsBomList" :key="item.id" :value="item.id">
                {{item.nodename}}
              </option>
            </select>
          </span>
        </li>
        <li>
          <p>
            {{$t('process_type')}}:
          </p>
          <span>
            <input id="tmpprocess" disabled="disabled" class="width150" maxlength="32" v-model="updKitsDto.process" />
          </span>
        </li>
        <li class="kits_date3">
          <p>
            {{$t('created_date')}}:
          </p>
          <span>
            <input type="text" id="tmpProductdate" class="width150" disabled="disabled" maxlength="16" v-model="updKitsDto.productdate" />
          </span>
          <a href="javascript:;" onclick="new Calendar().show(document.getElementById('tmpProductdate'));"><img src="/static/images/date.png" /></a>
        </li>
        <li>
          <p>Carrier lifetime:</p>
          <span>
            <input type="text" v-model="updKitsDto.carrierlifehrs" id="carrierlifehrs" theme="simple" cssClass="width150" maxlength="8" />hrs
          </span>
        </li>
        <li>
          <p>Carrier lifetime:</p>
          <span>
            <input type="text" v-model="updKitsDto.carrierlifewfrs" id="carrierlifewfrs" theme="simple" cssClass="width150" maxlength="8" />wfrs
          </span>
        </li>
        <div id="majorpartsDiv">
          <li v-for="item in updKitsDto.majorPartsList" :key="item.id">
            <p>
              {{item.nodename}} lifetime:</p>
            <span>
              <input type="hidden" name="tmpHeadid" :value="item.id" />
              <input type="text" name="tmpHeadhrs" class="width150" maxlength="8" v-model="item.hrsval" />hrs
            </span>
          </li>
          <li>
            <p>
              <s:property value="nodename" /> lifetime:</p>
            <span>
              <input type="text" name="tmpHeadwfr" class="width150" maxlength="8" :value="item.wfrval" />wfrs
            </span>
          </li>
        </div>
        <li>
          <p>
            {{$t('status')}}:
          </p>
          <span>
            <select class="width150" v-model="updKitsDto.kitsresult" id="kitsresult">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <s:iterator id="kitsStatusList" value="" status="st2">
                <option v-for="item in kitsStatusList" :key="item.key" :value="item.key">
                  {{$t(item.val)}}
                </option>
              </s:iterator>
            </select>
          </span>
        </li>
        <li>
          <p>
            {{$t('equipment_id')}}:
          </p>
          <span>
            <select class="width150" v-model="updKitsDto.equipmentid" id="equipmentid" onchange="selectEquipment(this, {{updKitsDto.id}} );">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <option v-for="item in equipmentList" :value="item.id" :key="item.id">
                {{item.equipmentnameequipmentList}}
              </option>
            </select>
          </span>
        </li>
        <li>
          <p>
            {{$t('chamber')}}:
          </p>
          <span>
            <select class="width150" v-model="updKitsDto.location">
              <option value="" selected="selected">
                {{$t('please_select')}}
              </option>
              <option v-for="item in locationList" :value="item" :key="item">
                {{item}}
              </option>
            </select>
          </span>
        </li>
        <li class="kits_img" style="display: none;">
          <p>Photo:</p>
          <span>
            <!--<img src="<s:property value="updKitsDto.pic_url"/>" />-->
          </span>
        </li>
        <li style="display: none;">
          <p></p>
          <span>
            <input type="file" name="addPicFile" id="addPicFile" class="width160" />
          </span>
        </li>
      </form>
    </ul>
    <div class="twobutton">
      <span class="setting_cancel"><a href="/kits/showKitsManageAction.action">Cancel </a> </span>
      <span class="kits_save"><a href="javascript:void(0);" onclick="upd();">Save to creat code</a></span>
    </div>
    <div class="clear"></div>
  </div>
</template>
<script>
export default {
  name: "editK"
};
</script>

