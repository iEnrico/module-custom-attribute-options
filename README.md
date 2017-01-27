# module-custom-attribute-options
Associate image/description to attribute options

# I leave you an example to observe the image and description in a advanced search results:

# <div class="advanced-search-summary">
    <?php $searchCriterias=$this->getSearchCriterias(); ?>
	    <?php //var_dump($searchCriterias); ?>
	        
        <?php foreach (array('left', 'right') as $side): ?>
            <?php if(@$searchCriterias[$side]): ?>
                <ul>
                    <?php foreach($searchCriterias[$side] as $criteria): ?>
                    
					<?php if ($criteria['name'] == 'Manufacturer'){ ?>
					
					<?php $marca_result=$criteria['value'];?>
					<?php $brandname = Mage::getResourceModel('eav/entity_attribute_option')->getAttributeOptionBrandname();?>
					<?php $marca_result_id =$brandname[$marca_result]; ?>
								
			        <?php $images = Mage::getResourceModel('eav/entity_attribute_option')->getAttributeOptionImages();?>
					<?php $marca_desc = Mage::getResourceModel('eav/entity_attribute_option')->getAttributeOptionDescriptions();?>

					<div class="pre-header-aca">
						<div class="img-aca">
							<img src="<?php echo $images[$marca_result_id]; ?>"/>
						</div>
						<div class="desc-aca"><?php echo $marca_desc[$marca_result_id]; ?></div>
					</div>
					
					
					<?php } ?>
					
					
                    <?php endforeach; ?>
                </ul>
            <?php endif; ?>
        <?php endforeach; ?>
</div>

/* Here I leave a example to see the image and description in a product view*/

<?php 
		$col =  $product->getAttributeText('manufacturer'); echo "Marca:".$col ."</br>";
 		
 		
 		$attr_manu = 'manufacturer';
		$attr_manu = $_product->getResource()->getAttribute($attr_manu);
		if ($attr_manu->usesSource()) {
		    $marca_id = $attr_manu->getSource()->getOptionId($col);
		}

        $images = Mage::getResourceModel('eav/entity_attribute_option')->getAttributeOptionImages();
		//echo "url:" . $images[$marca_id]."</br>";

		$marca_desc = Mage::getResourceModel('eav/entity_attribute_option')->getAttributeOptionDescriptions();
		echo "descripción:" . $marca_desc[$marca_id]."</br>";
		
		?>
		<img src="<?php echo $images[$marca_id]; ?>" />

