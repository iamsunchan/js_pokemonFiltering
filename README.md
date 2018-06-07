// define selected css class
jQuery('head').append('<style>.selected{border:3px solid deepskyblue;}</style>');

jQuery('.filter-button').off();

var All = jQuery('span[data-key="all"]');
var G1  = jQuery('.pkmfilter-table').eq(0).find('.filter-button').not('#gen-1, #gen-2, #gen-3, span[data-key="all"]');
var G2  = jQuery('.pkmfilter-table').eq(0).find('#gen-1, #gen-2, #gen-3');
var G3  = jQuery('.pkmfilter-table').eq(1).find('.filter-button');
var G4  = jQuery('.pkmfilter-table').eq(2).find('.filter-button');
var G5  = jQuery('.pkmfilter-table').eq(3).find('.filter-button');

All.addClass('selected');

All.on('click', function(){
  if (!jQuery(this).hasClass('selected')) jQuery(this).toggleClass('selected');
  jQuery('.selected').not(All).removeClass('selected');
  jQuery('#tbl_pokedex tbody tr').show();
});

G1.each(function(){
  jQuery(this).on('click', function(){
    All.removeClass('selected');
    jQuery(this).toggleClass('selected');
    filterRows();
  });
});

G2.each(function(){
  jQuery(this).on('click', function(){
    All.removeClass('selected');
    if (jQuery(this).hasClass('selected')) {
      jQuery(this).removeClass('selected');
    } else {
      G2.each(function(){
        jQuery(this).removeClass('selected');
      });
      jQuery(this).toggleClass('selected');
    }
    filterRows();
  });
});

G3.each(function(){
  jQuery(this).on('click', function(){
    All.removeClass('selected');
    if (jQuery(this).hasClass('selected')) {
      jQuery(this).removeClass('selected');
    } else {
      G3.each(function(){
        jQuery(this).removeClass('selected');
      });
      jQuery(this).toggleClass('selected');
    }
    filterRows();
  });
});

G4.each(function(){
  jQuery(this).on('click', function(){
    All.removeClass('selected');
    if (jQuery(this).hasClass('selected')) {
      jQuery(this).removeClass('selected');
    } else {
      G4.each(function(){
        jQuery(this).removeClass('selected');
      });
      jQuery(this).toggleClass('selected');
    }
    filterRows();
  });
});

G5.each(function(){
  jQuery(this).on('click', function(){
    All.removeClass('selected');
    if (jQuery(this).hasClass('selected')) {
      jQuery(this).removeClass('selected');
    } else {
      G5.each(function(){
        jQuery(this).removeClass('selected');
      });
      jQuery(this).toggleClass('selected');
    }
    filterRows();
  });
});

function filterRows() {
  var dataRows = jQuery('#tbl_pokedex tbody tr');
  dataRows.hide();

  var selectedArray = [];

  G1.each(function(){
    if (jQuery(this).hasClass('selected')) {
      selectedArray.push(jQuery(this).data('key'));
    }
  });

  G2.each(function(){
    if (jQuery(this).hasClass('selected')) {
      selectedArray.push(jQuery(this).data('key'));
    }
  });

  G3.each(function(){
    if (jQuery(this).hasClass('selected')) {
      selectedArray.push(jQuery(this).data('key'));
    }
  });

  G4.each(function(){
    if (jQuery(this).hasClass('selected')) {
      selectedArray.push(jQuery(this).data('key'));
    }
  });

  G4.each(function(){
    if (jQuery(this).hasClass('selected')) {
      selectedArray.push(jQuery(this).data('key'));
    }
  });

  dataRows.each(function(){
    var rowClasses = jQuery(this).attr('class').split(' ');
    var showRow = false;
    jQuery.each(selectedArray, function(index, item){
      if (rowClasses.indexOf(item) != -1) {
        showRow = true;
      }
    });
    if (showRow) jQuery(this).show();
  });

  if (jQuery('.selected').length == 0) {
    All.addClass('selected');
    jQuery('#tbl_pokedex tbody tr').show();
  }

  console.log(selectedArray);

}
