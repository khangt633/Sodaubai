<!DOCTYPE html>
<html lang="en"><head>
  <title>Sổ đầu bài</title>
<?php require('headerfirst.php') ?>

<body>
  <?php require('header.php') ?>
  <div class="container">
  <div class="col-xs-8"><h4> <b>SỔ ĐẦU BÀI</b></h4></div>
  <div class="col-xs-4 text-right">

 <?php require('lopvanamhoc.php') ?>
  </div>
  </div>
  <div class="container">
    <div class="col-xs-6">
  <ul class="nav navbar-nav">
        <li><a href="#"><span class="glyphicon glyphicon-question-sign"></span> Giúp</a></li>
    </ul>
      </div>
    <div class="col-xs-6">
       <?php 
      //lay uri
      $uri=$_SERVER['REQUEST_URI'];
      $uri= explode('/', $uri);
      $tranghientai=end($uri); 
      ?>
     
       <?php if ($tranghientai == 1)
        {  ?>
          
        <?php } 
        else { ?>

   <a class=" w3-right w3-btn" href="<?php echo base_url() ?>sdb/page/<?= $tranghientai-1 ?>"> ❮ Trước</a>
      
      <?php } ?>
      

    <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown">Tuần <?= $tranghientai ?>
  <span class="caret"></span></button>
  <ul class="dropdown-menu">
   <?php for ($i = 1; $i <= $sotrang; $i++) {
        ?> 
        <?php if ($i == $tranghientai)
        {  ?>
          <li class="list-group-item active"> Tuần <?= $i ?></li>
        <?php } 
        else { ?>

         <li > <a href="<?php echo base_url() ?>sdb/page/<?= $i ?>">Tuần <?= $i ?></a></li>
      
      <?php } ?>

    <?php
     } ?>

  </ul>
     
      <?php if ($tranghientai == $sotrang)
        {  ?>
          
        <?php } 
        else { ?>

         <a class=" w3-right w3-btn" href="<?php echo base_url() ?>sdb/page/<?= $tranghientai+1 ?>"> Sau ❯</a>
      
      <?php } ?>
    </div>  
  </div>
  <div class="container">
  <table class="table-bordered">
  <thead>
    <tr>
          <th scope="col" class="paddingtable">Y/m/d</th>
  <th scope="col" class="paddingtable">Tiết</th>
      <th scope="col" class="paddingtable">Buổi</th>
      <th scope="col" class="paddingtable">Môn học</th>
      <th scope="col" class="paddingtable">Tiết theo PPCT</th>
  <th scope="col" class="paddingtable">Tên bài dạy</th>
      <th scope="col" class="paddingtable">Nhận xét</th>
      <th scope="col" class="paddingtable">Xếp loại giờ học</th>
            <th scope="col" class="paddingtable">Giáo viên</th>
    </tr>
  </thead>
  <tbody>
    <?php $count_xs = 0;
    $count_tot = 0;
    $count_kha = 0;
    $count_tb = 0;
    $count_yeu = 0; ?>
    <?php foreach ($mangkq as $key => $value): ?>
    <tr>
        <td> <?= $value['ngay'] ?></td>
      <td><?= $value['tiet'] ?></td>
      <td><?= $value['buoi'] ?></td>
      <td><?= $value['monhoc'] ?></td>
    <td><?= $value['ppct'] ?></td>
      <td><?= $value['ndcv'] ?></td>
    <td><?= $value['nhanxet'] ?></td>
      <td><?= $value['xlgh'] ?></td>
            <td><?= $value['gv'] ?></td>
    </tr>
    <?php if ($value['xlgh'] == 'Xuất sắc')
    {
        $count_xs =  $count_xs + 1;
    }
    ?>
        <?php if ($value['xlgh'] == 'Tốt')
    {
        $count_tot =  $count_tot + 1;
    }
    ?>
    <?php if ($value['xlgh'] == 'Khá')
    {
        $count_kha =  $count_kha + 1;
    }
    ?>
    <?php if ($value['xlgh'] == 'Trung bình')
    {
        $count_tb =  $count_tb + 1;
    }
    ?>
    <?php if ($value['xlgh'] == 'Yếu')
    {
        $count_yeu =  $count_yeu + 1;
    }
    ?>


      <?php endforeach ?>
          <?php echo 'Số ngày xuất sắc: ', $count_xs;
          echo ' </br>
          Số ngày khá: ', $count_tot; 
          echo ' </br>
          Số ngày tốt: ', $count_kha; 
          echo ' </br>
          Số ngày trung bình: ', $count_tb; 
          echo ' </br>
          Số ngày yếu: ', $count_yeu;   ?>
       

      
  </tbody>
</table>
</body>
</html>
