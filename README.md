# getting-checkboxes-data-from-table-and-submitting-the-data-to-text-field


<?php
$blink = 0;
include('header.php');
?>
<div class="container body">
    <div class="main_container">

        <div class="right_col" role="main">
            <section class="content-header">
                <h1> <small></small> </h1>
                <ol class="breadcrumb">
                    <li><a href="<?php echo base_url(); ?>index.php/CFController/viewhome"><i class="fa fa-Home"></i>Home</a></li>
                    <li class="active">CallFor Entry Screen</li>
                </ol>
            </section>
            <div class="row">

                <table id="example" class="display" cellspacing="0" width="100%">
                    <thead>
                        <tr>
                            <th class='col-name'><input type="checkbox" id="selectall"/></th>
                            <th>sl.no</th>
                            <th>unitid</th>
                            <th>unitname</th>

                        </tr>
                    </thead>
                    <tbody>
                        <?php
                        $sno = 1;
                        foreach ($result as $row) {
                            ?>
                            <tr>
                                <td>     <input type="checkbox" class="case" name="case" value="<?php echo $row->cf001_unitcode; ?>" /></td>
                                <td><?php echo $sno; ?></td>
                                <td><?php echo $row->cf001_unitcode; ?></td>
                                <td><?php echo $row->cf001_unitname; ?></td>
                            </tr>
                            <?php
                            $sno++;
                        }
                        ?>
                    </tbody>
                </table>

                <hr>
                <p><button id="case1" name="case1">Submit</button></p>


                <p><b>Selected rows data:</b>
                    <input type="text" id="selectedcheckbox_data"/></p>
            </div>
        </div>
    </div>
</div>
<?php
include('footer.php');
?>

<script>
    $(document).ready(function () {
        $("#selectall").click(function () {
            var checkAll = $("#selectall").prop('checked');
            if (checkAll) {
                $(".case").prop("checked", true);
            } else {
                $(".case").prop("checked", false);
            }
        });

        $(".case").click(function () {
            if ($(".case").length == $(".case:checked").length) {
                $("#selectall").prop("checked", true);
            } else {
                $("#selectall").prop("checked", false);
            }

        });

        $("#case1").click(function () {
//            alert();
            var favorite = [];
            $.each($("input[name='case']:checked"), function () {
//                alert($(this).val());
                favorite.push($(this).val());
            });
//            alert("My ids are: " + favorite.join(", "));
            $('#selectedcheckbox_data').val(favorite.join(", "));
        });

    });
    $("#example").dataTable();


</script>
