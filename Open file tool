obj = hou.node("/obj/")

geo_container = obj.createNode("geo")

file_node = geo_container.createNode("file")

file_path = hou.ui.selectFile()

file_parm = file_node.parm("file")
file_parm.set(file_path)

splitted_path = file_path.split("/")

file_name = splitted_path[-1]

geo_container.setName(file_name)
