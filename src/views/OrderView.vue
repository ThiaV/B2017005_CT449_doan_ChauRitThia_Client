<template>
    <section class="order-form m-4">
        <div class="container pt-4">
            <div class="row">
                <div class="col-12 px-4">
                    <h1>Đặt Hàng</h1>
                    <span>Tự tin lên nào</span>
                    <hr class="mt-1" />
                </div>

                <div class="col-12">
                    <div class="row mx-4">
                        <!-- <div class="col-12">
                            <label class="order-form-label">Tên</label>
                        </div> -->
                        <div class="col-sm-6">
                            <div class="form-outline">
                                <input type="text" id="form1" class="form-control order-form-input" />
                                <label class="form-label" for="form1">Họ Tên</label>
                            </div>
                        </div>
                       
                    </div>

                    <div class="row mt-3 mx-4">
                        <div class="col-12">
                            <label class="order-form-label">Email</label>
                        </div>
                        <div class="col-12">
                            <div class="form-outline">
                                <input type="text" id="form3" class="form-control order-form-input" />
                            </div>
                        </div>
                    </div>

                    <!-- <div class="row mt-3 mx-4">
                        <div class="col-12">
                            <label class="order-form-label">Another type of thing you want to order</label>
                        </div>
                        <div class="col-12">
                            <div class="form-outline">
                                <input type="text" id="form4" class="form-control order-form-input" />
                            </div>
                        </div>
                    </div> -->

                    <!-- <div class="row mt-3 mx-4">
                        <div class="col-12">
                            <label class="order-form-label" for="date-picker-example">Date</label>
                        </div>
                        <div class="col-12">
                            <div class="form-outline datepicker" data-mdb-toggle-button="false">
                                <input
                                type="text" class="form-control order-form-input" id="datepicker1" data-mdb-toggle="datepicker" />
                                <label for="datepicker1" class="form-label">Select a date</label>
                            </div>
                        </div>
                    </div> -->

                    <div class="row mt-3 mx-4">
                        <div class="col-12">
                            <label class="order-form-label">Địa Chỉ</label>
                        </div>
                        <div class="col-12">
                            <div class="form-outline">
                                <input type="text" id="form5" class="form-control order-form-input" />
                                <label class="form-label" for="form5">Xã/Thị Trấn</label>
                            </div>
                        </div>
                        <div class="col-12 mt-2">
                            <div class="form-outline">
                                <input type="text" id="form6" class="form-control order-form-input" />
                                <label class="form-label" for="form6">Huyện</label>
                            </div>
                        </div>
                        <div class="col-sm-6 mt-2 pe-sm-2">
                            <div class="form-outline">
                                <input type="text" id="form7" class="form-control order-form-input" />
                                <label class="form-label" for="form7">Thành Phố</label>
                            </div>
                        </div>
                        <!-- <div class="col-sm-6 mt-2 ps-sm-0">
                            <div class="form-outline">
                                <input type="text" id="form8" class="form-control order-form-input" />
                                <label class="form-label" for="form8">Region</label>
                            </div>
                        </div> -->
                        <!-- <div class="col-sm-6 mt-2 pe-sm-2">
                            <div class="form-outline">
                                <input type="text" id="form9" class="form-control order-form-input" />
                                <label class="form-label" for="form9">Postal / Zip Code</label>
                            </div>
                        </div>
                        <div class="col-sm-6 mt-2 ps-sm-0">
                            <div class="form-outline">
                                <input type="text" id="form10" class="form-control order-form-input" />
                                <label class="form-label" for="form10">Country</label>
                            </div>
                        </div>-->
                    </div>

                    <!-- <div class="row mt-3 mx-4">
                        <div class="col-12">
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" />
                                <label class="form-check-label" for="flexCheckDefault">I know what I need to know</label>
                            </div>
                        </div>
                    </div> -->

                    <div class="row mt-3">
                        <div class="col-12">
                            <button type="button" id="btnSubmit" class="btn d-block btn-primary font-weight-bold mx-auto btn-submit cursor-pointer px-12 py-3 rounded-md text-black text-2xl f-1">Đặt Hàng Nào</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
<script>
export default {
    
}
</script>