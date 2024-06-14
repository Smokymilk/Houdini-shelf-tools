#method that returns a list of selected nodes
if not hou.selectedNodes():      
       print("No selected nodes")

else: #for all chosing nodes
       root = hou.node("/obj/")
for curnode in hou.selectedNodes():  #for current node in chosing list
    name="REN_"+curnode.name()
    curType = curnode.type().name()
    if hou.node("/obj/"+name):
       hou.node("/obj/"+name).destroy()
    if curType != "geo" and curnode.relativePathTo(root) == "../..":
       if curType != "object_merge":
         node=root.createNode("geo",name) #create new geo node
         merge=node.createNode("object_merge") #create inside object merge
         merge.parm("objpath1").set(curnode.path()) #set the parameter = path to the source node
         merge.parm('xformtype').set(1)
         node.moveToGoodPosition()
         red = hou.Color((1.0, 0, 0))
         node.setColor(red) 
       else:
                print("Wrong object")
    else:
            print("Select nodes inside Geometry context")
