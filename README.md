PickerView-Implementation
=========================
Picker view implemntation in iOS 6 or later

Follow the below steps for implementation.

1. Drag your picker view controller from Object library to your MVC. (Can be a Single View application or StoryBoard)
2. Invoke the UIPickerView Delegate and Datasource in header file. (Can drag and map in MVC)
3. Use the header and implementation code attached here as reference.



The Following code to be added to your Implementation(.m) file:

-(NSInteger) numberOfComponentsInPickerView:(UIPickerView *)pickerView{
    return 3;
}

-(NSInteger)pickerView:(UIPickerView *)pickerView numberOfRowsInComponent:(NSInteger)component
{
    if (component == TYPE) {
        return [arrayType count];
    }
    
    if (component == STATUS) {
    return [arrayStatus count];
    }
    
    if (component == Groups) {
         return [user.groups  count];
    }
    
    return 0;
}

-(NSString *) pickerView:(UIPickerView *)pickerView titleForRow:(NSInteger)row forComponent:(NSInteger)component
{
    
    if (component == TYPE) {
        return [arrayType objectAtIndex:row];
    }
    
    if (component == STATUS) {
        return [arrayStatus objectAtIndex:row];
    }
    
    if (component == Groups) {
         return [[user.groups objectAtIndex:row] groupName]; 
    }
   
    
    return 0;
}

-(void) pickerView:(UIPickerView *)pickerView didSelectRow:(NSInteger)row inComponent:(NSInteger)component
{
    groupsField.text=[[user.groups objectAtIndex:[pickerView selectedRowInComponent:0]] groupName];
    typeField.text=[arrayType objectAtIndex:[pickerView selectedRowInComponent:1]];
    statusField.text=[arrayStatus objectAtIndex:[pickerView selectedRowInComponent:2]];
    
}
