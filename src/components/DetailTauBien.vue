<template>
  <div>

    <hang-hai-detail-thong-tin-tau-bien
    v-if="code === 'DanhSachTauBien'"
    :type="type"
    ref="detailTauBien"
    :documentName="documentName"
    :documentYear="documentYear"
    :documentTypeCode="documentTypeCode"
    ></hang-hai-detail-thong-tin-tau-bien>

    <hang-hai-detail-hanh-trinh-phuong-tien
      v-if="code === 'DanhSachPhuongTienThuyNoiDia'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></hang-hai-detail-hanh-trinh-phuong-tien>

    <danh-sach-neo-tau
      v-if="code === 'Danh_sach_neo_dau'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-neo-tau>

    <danh-sach-ha-xuog
      v-if="code === 'Danh_sach_ha_xuong'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-ha-xuog>

    <danh-sach-sua-chua-tau
      v-if="code === 'Danh_sach_sua_chua_tau'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-sua-chua-tau>

    <danh-sach-tau-di-chuyen
      v-if="code === 'Danh_sach_tau_di_chuyen'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-tau-di-chuyen>

    <danh-sach-thu-tau
      v-if="code === 'Danh_sach_thu_tau'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-thu-tau>

    <danh-sach-giu-tau
      v-if="code === 'Danh_sach_giu_tau'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-giu-tau>
    <danh-sach-ghi-chu-canh-bao
      v-if="code === 'Danh_sach_giu_tau'"
      :type="type"
      ref="detailTauBien"
      :documentName="documentName"
      :documentYear="documentYear"
      :documentTypeCode="documentTypeCode"
    ></danh-sach-ghi-chu-canh-bao>
  </div>
</template>

<script>
import HangHaiDetailThongTinTauBien from './hang_hai/hanghai_detail_thong_tin_tau_bien.vue'
import HangHaiDetailHanhTrinhPhuongTien from './hang_hai/hanghai_detail_hanh_trinh_phuong_tien.vue'
import DanhSachHaXuong from './hang_hai/DanhSachHaXuong.vue'
import DanhSachNeoTau from './hang_hai/DanhSachNeoTau.vue'
import DanhSachSuaChuaTau from './hang_hai/DanhSachSuaChuaTau.vue'
import DanhSachTauDiChuyen from './hang_hai/DanhSachTauDiChuyen.vue'
import DanhSachThuTau from './hang_hai/DanhSachThuTau.vue'
import DanhSachDuTau from './hang_hai/DanhSachDuTau.vue'
import DanhSachGhiChuCanhBao from './hang_hai/DanhSachGhiChuCanhBao.vue'

export default {
  props: ['code', 'type', 'documentName', 'documentYear', 'documentTypeCode'],
  components: {
    'hang-hai-detail-thong-tin-tau-bien': HangHaiDetailThongTinTauBien,
    'hang-hai-detail-hanh-trinh-phuong-tien': HangHaiDetailHanhTrinhPhuongTien,
    'danh-sach-neo-tau': DanhSachNeoTau,
    'danh-sach-ha-xuog': DanhSachHaXuong,
    'danh-sach-sua-chua-tau': DanhSachSuaChuaTau,
    'danh-sach-tau-di-chuyen': DanhSachTauDiChuyen,
    'danh-sach-thu-tau': DanhSachThuTau,
    'danh-sach-giu-tau': DanhSachDuTau,
    'danh-sach-ghi-chu-canh-bao': DanhSachGhiChuCanhBao
  },
  data: () => ({
    detail_model: {}
  }),
  created () {
    let vm = this
    vm.$nextTick(function () {
      vm.reloadDetail()
    })
  },
  watch: {
    '$route': function (newRoute, oldRoute) {
      let vm = this
      let query = newRoute.query
      if (query.hasOwnProperty('renew')) {
        vm.reloadDetail()
      }
    }
  },
  methods: {
    reloadDetail: function () {
      var vm = this
      if (vm.code === 'DanhSachTauBien') {
        let detailTauBien = vm.$refs.detailTauBien
        if (detailTauBien !== null && detailTauBien !== undefined && detailTauBien !== 'undefined') {
          detailTauBien.loadDetailTauBien()
        }
      } else if (vm.code === 'DanhSachPhuongTienThuyNoiDia') {
        let detailPhuongTienThuyNoiDia = vm.$refs.detailPhuongTienThuyNoiDia
        if (detailPhuongTienThuyNoiDia !== null && detailPhuongTienThuyNoiDia !== undefined && detailPhuongTienThuyNoiDia !== 'undefined') {
        }
      }
    }
  }
}
</script>
