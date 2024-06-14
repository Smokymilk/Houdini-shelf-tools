#get the obj
obj = hou.node("/obj/")
#create geo_container
geo_container = obj.createNode("geo")
#create nodes
alembic_node = geo_container.createNode("alembic")
unpack_node = geo_container.createNode("unpack")
convert_node = geo_container.createNode("convert")
matchsize_node = geo_container.createNode ("matchsize")
null_node = geo_container.createNode("null")


##set_inputs
unpack_node.setInput(0, alembic_node, 0)
convert_node.setInput(0, unpack_node, 0)
matchsize_node.setInput(0, convert_node, 0)
null_node.setInput(0, matchsize_node, 0)
geo_container.layoutChildren()

#create centroid
node_type = hou.sopNodeTypeCategory().nodeType("matchsize")

nodes = node_type.instances()

for node in nodes:
    node.parm("justify_y").set(1)

#set flags
null_node.setDisplayFlag(True)
alembic_node.setRenderFlag(False)


#rename geo
file_path = hou.ui.selectFile()

file_parm = alembic_node.parm("fileName")
file_parm.set(file_path)

splitted_path = file_path.split("/")

file_name = splitted_path[-1]

geo_container.setName(file_name)
# renaming the node null 
null_name = file_name.split(".")[-2]  
null_node.setName("OUT_" + null_name) 

# repainting the null node in black
red = hou.Color((0.0, 0.0 , 0.0)) 
null_node.setColor(red)
# reshape the null node
null_node.setUserData("nodeshape", "circle")

#transform in network
geo_container.moveToGoodPosition()
