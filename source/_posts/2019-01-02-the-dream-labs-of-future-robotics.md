title: The Dream Labs of Future Robotics
date: 2019-01-02
updated: 2019-10-08
categories:
- [IR]
tags: 
- CMU
- HRI
- Robot Manipulation
- Robot Grasping
- Robotic Legged Locomotion
- Robot Learning
- Stanford
- OpenAI
---

首先翻译关于CMU RI的介绍https://www.ri.cmu.edu/the-dream-labs-of-future-robotics/， 然后再介绍几个同样在世界最前沿的研究AI + Robotics的实验室的相关信息...<!--more-->

随着AI的火热，AI+机器人的融合再次成为前沿研究方向 ： 主要是融合 **Machine Learning(Deep Learning)， Computer Vision，Robotics** 三个方向，目标是 能够理解Real World，并与之交互的自主机器人。新的研究有新的概念，比如Robot Vision，Robot Learning。主要研究机构是几个一流大学：Stanford，CMU，UC Berkeley，MIT，Princeton 及 大公司研究Lab ： OpenAI，DeepMind, 腾讯 Robotics X...

# [CMU RI](https://www.ri.cmu.edu/)
翻译 : CMU RI : 创造未来机器人的梦想实验室

The Dream Labs of Future Robotics
创造未来机器人的梦想实验室

by Tanya M. Anandan, Contributing Editor
Robotic Industries Association Posted 10/30/2018

Tomorrow’s robotics are taking shape in today’s labs. From package delivery robots and self-driving cars, to surgical snakes and search and rescue robots, the innovations have profound implications. A year, 3 years, or maybe 5 to 10 years down the road, they could be at our door, in our home, or at our side when we need them most.
不久的将来的机器人雏形正在当下的实验室里诞生。从快递机器人和自动驾驶汽车，到外科手术机器蛇和搜救机器人，这些创新具有巨大的影响力。1年，3年，也许5到10年以后，他们将逐渐出现在大众的社区里，家里，或者任何人们需要的地方。

We will take a peek into our future through the lens of a few of the nation’s top academic institutions for robotics research. Each of these universities continues to attract and recruit renowned faculty to their robotics rosters. They have interdisciplinary master’s and doctoral programs in robotics. They spawn successful spinoffs and notable alumni that shake up the industry. They embrace a comprehensive approach to robotics research and education.
我们将通过美国一些顶尖的机器人研究学术机构的视角来展望我们的未来。每一所大学都在继续吸引和招募著名的教员加入它们的机器人科研队伍。它们有跨学科的机器人硕士和博士项目。它们孵化出成功的衍生品和撼动整个行业的知名校友。它们采用了一种全面的方法进行机器人研究和教育。

As we’ve said before, robotics is a multidisciplinary sport. The traditional areas of study, mechanical engineering, electrical engineering and computer science, have broadened into biological systems and cognitive science. Many of the top university robotics programs are attacking robotics challenges from all angles and making fascinating discoveries along the way.
如我们此前所说，机器人是一项多学科交叉的领域。已经从机械工程ME，电子工程EE和计算机科学CS 这些传统研究领域扩展到生物系统和认知科学。许多顶尖的大学机器人项目正从各个角度尝试解决机器人面临的挑战，并在此过程中取得了令人瞩目的发现。

## Human-Robot Interaction 人机交互
Established in 1979, the Robotics Institute at Carnegie Mellon University (CMU) is one of the oldest in the country and the first to offer graduate programs in robotics. The institute encompasses the main facility on CMU’s campus in Pittsburgh, Pennsylvania, the National Robotics Engineering Center (NREC) in nearby Lawrenceville, and Robot City in Hazelwood with its 40 acres of robot testing fields at the site of a former steel mill. The university and the Greater Pittsburgh robotics scene have transformed the Steel City into Roboburgh, one of the well-established hubs we visited in a previous article on Robotics Clusters the Epicenter for Startups.
卡内基梅隆大学(CMU)机器人研究所成立于1979年，是美国历史最悠久的机器人研究所之一，也是第一个开设机器人专业研究生课程的机构。该研究所包括位于宾夕法尼亚州匹兹堡市CMU校园内的主要设施、位于劳伦斯维尔附近的国家机器人工程中心(NREC)以及黑兹伍德的机器人城(Robot City)。这所大学和更大的匹兹堡机器人领域已经把这座钢铁之城变成了Roboburgh，这是我们[之前文章](http://bit.ly/28MERp2)里访问过的一个久负盛名的中心城市。

The Robotics Institute is under the CMU School of Computer Science. Researchers take a comprehensive approach to robotics, studying robot design and control, perception, robot learning, autonomy, and human-robot interaction (HRI).
机器人研究所隶属于CMU计算机科学(Computer Science)学院。研究人员采用综合方法研究机器人，研究机器人设计和控制，感知，机器人学习，自主化，和人机交互(HRI)。

In fact, a central theme according to Martial Hebert, the institute’s director, is HRI. “Much of the work in robotics has less to do with robots. It has to do with people,” he says. “Understanding people, predicting people, and understanding their intentions. Everything from understanding pedestrians for self-driving cars, to understanding coworkers in collaborative robot manufacturing, any application that involves interaction with people at any level.”
事实上，根据该研究所所长Martial Hebert的说法，HRI是中心主题。“机器人技术的大部分工作都与机器人无关，而与人有关。“理解，预测人类，理解他们的意图。从理解自动驾驶汽车中行人的行为，到理解协作机器人制造中的人类协作者，涉及到各种场景中的各种人的交互。

One of the ways CMU is trying to better understand people is by studying our body language. Researchers built a life-sized geodesic dome equipped with VGA cameras, HD cameras, and depth sensors to capture images from tens of thousands of trajectories. The result is dynamic 3D reconstruction of people, their body poses, and motions.
CMU正在尝试的一种方式是，通过研究我们的肢体语言来更好的理解人类。研究人员建造了一个真人大小的测地穹顶，配有VGA摄像机、高清摄像机和深度传感器，可以从数万条轨迹中捕捉图像。其结果是动态三维重建的人体模型，他们的姿态和运动信息。
> 这说的是OpenPose : https://github.com/CMU-Perceptual-Computing-Lab/openpose

As humans, we speak volumes through our body movements, posture, and facial expressions without needing to utter a word. The CMU Panoptic Studio was built to capture these subtle nonverbal cues and create a database of our body language to help robots better relate to humans. The research is ongoing with datasets now available for full-body motions, hand gestures, and 3D facial expressions.
作为人类，我们即使不说一个字，仅仅通过身体的动作、姿势和面部表情就能表达很多信息。[CMU Panoptic Studio](http://domedb.perception.cs.cmu.edu/)的建立就是为了捕捉这些微妙的非语言信息，从而创建一个我们的肢体语言[数据库](http://bit.ly/2qq0EL3)，以帮助机器人更好地与人类交流。这项研究正在进行中，数据集现在可以用于全身运动、手势和三维面部表情。

Outside of academia, the work has not gone unnoticed. Facebook was inspired to open a lab in Pittsburgh and hired Yaser Sheikh, the CMU professor who developed the Panoptic Studio. It turns out nonverbal social interaction is just as important in the virtual world. Think Oculus Rift, the virtual reality technology now owned by Facebook.
在学术界之外，这项工作并没有被忽视。Facebook受到启发，在匹兹堡设立了一家[实验室](http://bit.ly/2Q36ZXK)，并聘请了开发Panoptic Studio的CMU教授亚瑟•谢赫(Yaser Sheikh)。事实证明，在虚拟世界中，非语言社交互动同样重要。想想Facebook的VR设备Oculus Rift就知道了。

## Machine Learning and Robot Intelligence 机器学习与机器人智能
Hebert says machine learning is another big area for CMU. The idea is to have a robot learn from its own actions and data, and learn to get better over time. Examples include manipulators that learn how to grasp, or drones that learn how to fly better. The recent collaboration between CMU and Honeywell Intelligrated to develop advanced supply chain robotics and AI will harness the power of machine learning to control and operate multiple robotic technologies in connected distribution centers.
赫伯特说：”机器学习是CMU的另一重点研究领域。“ 基本思路是让机器人从自己的动作和数据中学习，并随着时间的推移越来越强。例如，机械臂学习如何抓取物体，无人机学习如何自主飞行。CMU和霍尼韦尔最近合作开发了先进的[供应链机器人技术](http://bit.ly/2OXKeYQ)，人工智能将利用机器学习的力量来控制和操作互联的配送中心里的多种机器人。

“It’s a material handling application that includes sorting packages and moving packages around distribution centers at very high rates,” says Hebert, without divulging much about the robots they are using. A more recent Honeywell partnership with Fetch Robotics may provide a clue.
“这是一个物料处理应用，主要是在配送中心高速的分拣和搬运包裹，”赫伯特说，但没有透露他们使用的机器人的太多信息。霍尼韦尔最近与Fetch Robotics的合作可能提供了线索。

“We’re past the stage where robots only do repetitive operations,” he says. “They have to be able to make decisions, they have to be able to adapt to the environment. Things are not always in the same place or where they should be. That’s where machine learning and autonomy come into play. All of it comes together in this type of application.”
他说:“我们已经过了机器人只能执行重复性操作的阶段。”“现在它们必须能自主决策，必须能适应环境变化。物品并不总是在固定位置或者本应该在的位置。这就是机器学习和自主可以发挥作用的地方。当前主要集中在这种类型的应用上。"

The project is underway at the university’s NREC facility, where for over 20 years CMU researchers have helped conceptualize and commercialize robotic technologies for industrial and government clients. From laser paint removal robots for F-16 fighter jets to unmanned bomb-clearing vehicle convoys, to autonomous crop harvesters, construction loaders and mining robots, the impact has been felt across numerous industries. Watch this video to see NREC technology in action, such as this Caterpillar self-driving mining truck.
该项目正在该大学的NREC设施场所进行，在那里，CMU的研究人员帮助企业和政府客户概念化和商业化机器人技术已超过20年。从F-16战斗机的激光除漆机器人，到无人清弹车辆车队，再到自动收割机、建筑机器人和采矿机器人，许多行业都感受到了这种影响。[观看这段视频](http://bit.ly/2SsyDyW)可以看到NREC技术的实际应用，比如这款卡特彼勒的自动驾驶采矿车。

Despite CMU’s audacious world of autonomous vehicles, Hebert says they focus less on the physical aspect of robotics research compared to robot intelligence. This is a recurring theme we hear inside and outside academia, the attention on algorithms, or the software side of robotics. He offers an example.
尽管CMU拥有大量的自动驾驶交通装置，赫伯特说，与机器人智能相比，他们更少关注机器人研究的物理层面。这是一个反复出现的主题，我们在学术界和工业界都有耳闻，人们更关注算法，或者说机器人技术的软件部分。他举了一个例子。

Kaarta makes a 3D mobile scanning and mapping generation system that puts advanced simultaneous localization and mapping (SLAM) technology in the palm of your hand – in real time. The 3D digital model is generated right in front of you on a handheld touchscreen interface, without the need for post-processing. At its heart is the patent-pending advanced 3D mapping and localization algorithms, a product of CMU’s robotics lab.
Kaarta制造的3D手持扫描和地图生成系统，可以在手持设备上实现先进的实时同步定位和地图(SLAM)技术。3D数字模型将实时呈现在你面前的手持触摸屏界面上，而不需要后处理。它的核心是正在申请专利的高级3D地图和定位算法，这正是CMU机器人实验室的产品。

“Our contribution was to take massive amounts of data from the sensors and optimize it very quickly and efficiently,” says Hebert, crediting advanced mathematics and algorithms for the feat.
“我们的贡献是从传感器中获取大量数据，并快速高效地对其进行优化，”赫伯特说，他将这归功于先进的数学和算法。

Watch as Kaarta CEO Kevin Dowling demonstrates the system. He’s also a product of the doctoral program at CMU.
Kaarta的CEO凯文·道林演示了这个[系统](http://bit.ly/2Off8H4)。他也出自CMU博士项目。

The system’s compact size and customizable imaging hardware allow it to be mounted to ground or aerial vehicles, such as drones, for interior and exterior use. Right now, the company’s products are directed toward infrastructure inspectors, surveyors, engineers, architects and facilities planners. But imagine the possibilities for first responders, hazmat teams, law enforcement, and down the road, for self-driving cars.
该系统小巧的尺寸和可定制的成像硬件使其能够安装在地面或空中交通工具(如无人机)上，供内部和外部使用。目前，该公司的产品面向基建检查员、测量师、工程师、建筑师和设施规划者。想象一下，对急救人员、危险品小组、执法人员以及未来的自动驾驶汽车来说，同样也是适用的。

## Search and Rescue Robots 搜救机器人
Speaking of first responders, that brings us to a peculiar-looking robot developed in the labs at CMU. It goes where humans can’t.
说到急救人员，这让我们想到了一个在CMU实验室开发的奇特机器人。它能去人类不能去的地方

The Snakebot robot undulates its way into tight spaces and sticky situations, where the environment may be unhospitable and unpredictable for people, and even canines. Snakebot was on the ground for search and rescue efforts after a disastrous earthquake hit Mexico City last fall. Then this past spring, it was named Ground Rescue Robot of the Year.
蛇形机器人能在狭窄的空间和黏黏的环境中蜿蜒前行，那里的环境对人类甚至犬科动物来说都是不友好和不可预测的，甚至对犬科动物也是如此。去年秋天墨西哥城发生灾难性地震后，蛇形机器人就在地面上进行搜救工作。今年春天，它被评为年度地面救援机器人。[!img](https://www.ri.cmu.edu/wp-content/uploads/2018/10/Oct2018_Carnegie-Mellon-Snake-Robot7276.jpg)

Howie Choset, a professor of computer science and Director of the CMU Biorobotics Lab where Snakebot was developed, says they are proud of the robot and its accomplishments to date. Still, challenges remain.
计算机科学教授、蛇形机器人所在的CMU生物机器人实验室主任Howie Choset说，他们为这种机器人及其迄今取得的成就感到骄傲。尽管如此，挑战依然存在。

“The challenges are how to move (locomotion), where to move (navigation), creating a map of the environment, and providing the inspector with good remote situational awareness,” says Choset.
Choset说:“挑战在于如何移动(locomotion)，往哪里移动(navigation)，创建环境地图，以及为检查员提供良好的远程态势感知。”

A camera on the front of the robot helps an operator see the immediate area around the robot, but this has limitations in low-light conditions and highly cramped environments. In disaster scenarios, sensors for perceiving sound and smell may be more useful in detecting signs of life.
机器人的前置摄像头可以帮助操作人员看到机器人周围的邻近区域，但在低光条件和高度狭窄的环境中有局限性。在灾难场景中，感知声音和气味的传感器在探测生命迹象时可能更有用。

Watch CMU’s snake robot use its multi-joint body to climb poles, slither under fences, maneuver through pipes, roll into storm drains, and even swim.
观看CMU的[蛇形机器人视频：](http://bit.ly/2Riq4FI)用它的多关节身体爬杆，在栅栏下滑行，穿过管道，滚进雨水渠，甚至游泳。

Choset envisions snake robots destined for manufacturing applications such as inspecting tight spots inside aircraft wings, or installing fasteners inside airplane wings or boats, and painting inside car doors. He also hopes to see these snake bots at work in the nuclear industry.
Choset设想将蛇形机器人用于制造领域，比如检查机翼内部的紧密点，或在飞机机翼或船只内部安装紧固件，以及在车门内部油漆。他还希望看到这些蛇形机器人[在核工业中发挥作用](http://bit.ly/2yEXvLw)。

## Medical Robotics 医疗机器人
Another snake-like robot developed in the Biorobotics Lab has made significant headway in medical robotics, another noteworthy area of study for CMU. Unlike the snake robots used in search and rescue or industrial applications, the surgical snake is a cable-driven robot. Choset explains the difference.
在生物机器人实验室开发的另一个蛇形机器人在医学机器人领域取得了重大进展，这是CMU另一个值得关注的研究领域。与用于搜救或工业应用的蛇形机器人不同，外科手术蛇形机器人是一种电缆驱动的机器人。Choset解释了其中的区别。

“Imagine a marionette that has little wires that pull on different parts of the doll. A cable-driven robot is one where internal cables pull on the links to cause the joints to bend. The motors don’t have to be on board, so you can get away with a lighter mechanism, or in my case, use bigger motors.”
“想象一下，一个木偶有一根小电线，可以拉着娃娃的不同部位。由电缆驱动的机器人是由内部电缆拉动连接，使关节弯曲的机器人。马达不需要安装在机器上，所以你可以用更轻的机械装置，或者在我的情况下，用更大的马达。

This is in contrast to the locomoting robot that crawls through pipes, where all of the motors are on board.
这与在管道中爬行的移动机器人形成对比，在管道中所有的马达都在机器上。

“I think minimally invasive surgery is a great area for robotics,” says Choset. “The challenges are access, how to get to the right spots, and once you’re there, developing tools, end effectors and other mechanisms to deliver therapies and perform diagnostics. Situational awareness, or being able to really understand your surrounding environment, is the next step after that.”
Choset说:“我认为微创手术是机器人技术的一个重要领域。”“我们面临的挑战是如何到达正确的患处，一旦到达患处，就可以利用工具、末端执行器和其他机制提供治疗和执行诊断。情境感知，或者说能真正理解你周围的环境，是接下来的一步。”

The biorobotics team at CMU envisions minimally invasive no-scar surgery in the snake robot’s future. But in the meantime, the technology has already found success in transoral robotic surgery and has been licensed to Medrobotics Corporation. Professor Choset is a cofounder of the Massachusetts-based company. RIA will dive deeper into this technology next month when we focus on surgical robotics.
CMU的生物机器人团队设想在未来使用蛇形机器人进行微创无疤痕手术。但与此同时，这项技术已经在经口机器人手术中取得了成功，并已被授权给Medrobotics公司。Choset教授是这家总部位于马萨诸塞州的公司的联合创始人。下个月，当我们专注于外科机器人技术时，RIA将会深入研究这项技术。

When a robot is attached to the body or inside a human body, medical robotics takes human-robot interaction to new levels. But what about when humans are the robot’s passengers? That’s basically the scenario with self-driving cars. Let’s take a ride to the Motor City.
当机器人附着在[人体或人体内部](http://bit.ly/2kIfUzp)时，医疗机器人将人与机器人的交互提升到一个新的水平。但如果人类是机器人的乘客时呢?这就是自动驾驶汽车的基本应用场景。让我们去汽车城看看吧。


## Self-Driving Cars 无人驾驶汽车
The University of Michigan may be world renowned for its football program, but it is landmark self-driving vehicle research that put Michigan Robotics on the map – literally. Just 40 miles outside of Detroit, the Mcity Test Facility is a one-of-a-kind proving ground for testing connected, autonomous vehicle technologies in simulated urban environments.
密歇根大学(University of Michigan)或许因其橄榄球运动而闻名于世，但一个里程碑式的自动驾驶汽车研究让密歇根机器人(Michigan Robotics)登上了世界舞台。距底特律仅40英里，Mcity Test Facility是一个独一无二的试验场，用于在模拟的城市环境中测试网联自动驾驶汽车技术。

The 32-acre site on U-M’s campus in Ann Arbor has miles of roads with intersections, traffic signs and signals, sidewalks, simulated buildings, obstacles such as construction barriers, and even the occasional “dummy” to test pedestrian avoidance technology. It’s the quintessential outdoor lab for researchers envisioning a local network of connected autonomous vehicles by 2021.
位于安阿伯的U-M校区占地32英亩，拥有数英里长的道路，布满十字路口、交通标志，信号灯、人行道、模拟建筑、建筑障碍物，甚至偶尔还会有“假人”来测试行人避让技术。这是一个典型的户外实验室，研究人员希望到2021年建立一个网联自动驾驶汽车局域网络。

Watch as researchers demonstrate the advantages of connected self-driving vehicles and how augmented reality is helping them test these technologies more efficiently and safely.
研究人员展示了[网联自动驾驶汽车的优势](http://bit.ly/2CPnW4k)，以及AR如何帮助他们更高效、更安全地测试这些技术。

“Self-driving is probably what we’re known for the most,” says Dmitry Berenson, a professor of engineering at U-M. “That’s a real strength here. We have the U-M Transportation Research Institute (UMTRI) that has been conducting self-driving work for many years, even before it was popular. We’re very close to the auto manufacturers, so we can very quickly set up meetings and integrate with them, and get feedback. Well-established relationships with Toyota and Ford are pushing self-driving technology forward.”
密歇根大学工程学教授Dmitry Berenson表示:“对大众来说，我们这里最出名可能是自动驾驶。这是我们真正的优势。我们有U-M交通研究所(UMTRI)，在自动驾驶流行执行就已经开展了多年的研究工作。我们与汽车制造商关系密切，因此我们可以非常迅速地安排会议，与他们进行整合，并获得反馈。与丰田和福特建立的良好关系正在推动自动驾驶技术的发展。“

We first met Berenson when he was at Worcester Polytechnic Institute leading research in machine learning and manipulation planning. Back then, we were discussing his work with motion planning algorithms for a humanoid robot stacking boxes. Check out Our Autonomous Future with Service Robots. Now, Berenson is Director of the Autonomous Robotic Manipulation (ARM) Lab, which he founded two years ago when he joined U-M. Algorithms are still his passion.
我们第一次见到Berenson是在伍斯特理工学院领导机器学习和操作计划研究的时候。当时，我们正在讨论他的工作与运动规划算法的类人机器人堆叠盒。[让我们来看看我们的自动未来服务机器人](http://bit.ly/1pfBffs)。现在，Berenson是自主机器人操作(ARM)实验室的主任，该实验室是他两年前加入密歇根大学时创办的。算法仍然是他的激情所在。

“Michigan is doing something really important, which is pushing the boundaries on algorithms to get robots into unstructured environments in the real world,” says Berenson. “We have people working on this in terms of aerospace applications, all the way to legged locomotion, to manipulation like my group, to self-driving. There’s a huge push in self-driving technology. Some of our faculty have startups in this area.”
“密歇根正在做一件非常重要的事情，它正在推动算法的边界，让机器人进入现实世界的非结构化环境，”Berenson说。“我们中的一些人在研究航空航天机器人，一些人在研究[腿式机器人](http://bit.ly/2PtEjKu)，我的团队在研究机器人操控，还有人在研究自动驾驶。现在自动驾驶技术有了巨大的进展，我们的一些教授因此开始创业。”

U-M Professor Edwin Olson cofounded May Mobility in 2017. The startup’s autonomous shuttle service is currently operating in downtown Detroit and charting new territory in other Midwestern cities. As Director of the APRIL Robotics Lab, Olson is known for his work in perception algorithms, mapping, and planning. The licensed intellectual property behind these self-driving shuttles was developed in his lab.
密歇根大学的Edwin Olson森教授在2017年与人共同创立了May Mobility。这家初创公司的自主运输服务目前在底特律市中心运营，并在中西部其他城市开辟了[新市场](https://tcrn.ch/2DcqXwA)。作为APRIL机器人实验室的主任，Olson以他在感知算法、地图和规划方面的工作而闻名。这些自动驾驶运输背后的授权知识产权是在他的实验室开发的。

Replacing diesel buses in some cases, the six-passenger electric shuttles navigate city streets on specific routes in business districts, or on corporate and college campuses. This follows last year’s pilot in which May Mobility shuttled employees of Bedrock Detroit and parent company Quicken Loans between their offices and the city’s parking garages.
在某些情况下，这种[六人座的电动巴士](http://bit.ly/2CLyukZ)取代了柴油公交车，在城市街道的商业区、公司和大学校园的特定路线穿梭。在去年的试点项目中，May Mobility接送底特律基岩汽车公司(Bedrock Detroit)和母公司的员工，加快了他们的办公室与停车场之间的[通勤](https://www.ri.cmu.edu/wp-content/uploads/2018/10/Oct2018_May-Mobility-Autonomous-Shuttle.jpg)。

A surge in funding from major investors such as BMW i Ventures, Toyota AI Ventures, and Y Combinator, plus a new partnership with tier-one auto supplier Magna International, could accelerate a nationwide rollout for Olson’s autonomous shuttle startup.
来自宝马i Ventures、丰田AI Ventures和Y Combinator等主要投资者的资金激增，加上与一流汽车供应商麦格纳国际(Magna International)的新合作，可能会加速Olson的自主运输初创企业在全国的扩张。

Another U-M faculty member, Ryan Eustice, is Senior Vice President of Automated Driving at Toyota Research Institute. He’s known for his work in SLAM technology.
另一名U-M教员，Ryan Eustice，是丰田研究所自动驾驶高级副总裁。他以在SLAM技术领域的工作而闻名。

“SLAM is crucial technology for self-driving cars,” says Berenson. “They don’t know where they are without it.”
“SLAM 是自动驾驶汽车的关键技术，”Berenson说。“没有SLAM，汽车无法定位。”

Eustice is Director of the Perceptual Robotics Laboratory (PeRL), a mobile and marine robotics lab at U-M focused on algorithm development for robotic perception, navigation, and mapping. He worked on the Next Generation Vehicle (NGV) project with Ford Motor Company, the first automaker to test an autonomous vehicle at Mcity. SLAM meets snow, check it out.
Eustice是Perceptual机器人实验室(perception Robotics Laboratory，简称PeRL)的负责人，这是U-M的一个移动机器人实验室，专注开发机器人感知，导航和地图 算法。他与福特汽车公司(Ford Motor Company)合作开发了下一代汽车(NGV)项目，这是第一家在Mcity测试自动驾驶汽车的汽车制造商。[SLAM与雪](http://bit.ly/2Jpwr7b)。

## Robotics Raises the Roof
Ford has a legacy stake in Michigan Robotics. A $75 million facility currently under construction on the U-M Ann Arbor campus will be named the Ford Motor Company Robotics Building in recognition of the automaker’s $15 million gift to the engineering college. The 140,000-square-foot building will house a three-story fly zone for autonomous aerial vehicles, an outdoor obstacle course for legged robots, and a high-bay garage space for self-driving cars. Ford will also establish an on-campus research laboratory occupying the fourth floor, where the automaker’s researchers will be able to easily collaborate with the university’s faculty and provide hands-on experiences for students.
福特在Michigan Robotics有一笔捐赠。位于U-M安阿伯(Ann Arbor)校区的一座造价7500万美元的建筑将被命名为“福特汽车机器人大厦”(Ford Motor Company Robotics Building)，以回馈该公司向该校工程学院(engineering college)捐赠的1500万美元。这座占地14万平方英尺的建筑将容纳一个三层楼的自动驾驶飞行汽车飞行区、一个为腿式机器人设计的户外障碍训练场，以及一个为自动驾驶汽车设计的高隔间车库。福特还将在四楼建立一个校园研究实验室，在那里，福特的研究人员将能够轻松地与大学教授们合作，也为学生们提供实验机会。

The new facility will also include classrooms, offices and lab spaces. Bringing students, faculty and researchers together under one roof in a space dedicated to robotics will encourage fluent interaction and the exchange of ideas. In effect, a culture designed to study the problems and solutions of robotics from all angles, including mechanics, electronics, perception, control and navigation, an approach university leadership refers to as “full spectrum autonomy.” The building is slated for completion in early 2020.
新设施还包括教室、办公室和实验室。将学生、教师和研究人员聚集在一个致力于机器人技术的空间里，鼓励流畅的沟通和思想的碰撞。目的是塑造一种从机械、电子、感知、控制和导航等各个角度研究机器人技术问题和解决方案的文化。该建筑计划在2020年初完工。

Toyota Research Institute has also dedicated funding to U-M research efforts. “They value our robotics and self-driving technology not because they think it will advance their interests tomorrow, but 5 or 10 years down the road,” says Berenson. “My ARM Lab has one of these grants.”
丰田研究所也决定为U-M的研究提供资金支持。Berenson说:“他们投资我们的机器人技术和自动驾驶技术，看中的并不是近期而是未来5到10年内的回报。”“我的ARM实验室也得到这样的资助。”

## Robot Manipulation and Grasping 机器人操作与抓取
In his lab, Berenson is developing algorithms for robotic motion planning and manipulation. The research includes grasping in cluttered environments and manipulation of deformable objects, such as rope or cloth that are malleable and change shape when handled.
在他的实验室里，Berenson正在开发机器人运动规划和操作算法。这项研究包括在杂乱的环境中抓取，以及对可变形物体的操作，比如绳子或布料，这些物体具有延展性，在处理时可以改变形状。

“We have deformable objects, we have piles of clutter, some of which we may have seen before, some we haven’t. We have to manipulate them anyway,” says Berenson. “We can’t wait for someone to perfectly model the environment, and give us all the parameters and tell us where everything is, and provide a CAD model of every object. That’s great in a factory, but it won’t work in somebody’s home.
“我们有可变形的物体，有成堆的杂物，有些我们以前可能见过，有些我们没见过。”无论如何，我们必须操纵它们，”Berenson说。“我们不能等着有人对环境进行完美的建模，给我们所有的参数，告诉我们所有的东西在哪里，并提供每个对象的CAD模型。”这在工厂里很好，但在家庭环境中行不通。

“You will never have a perfect model of how this rope or cloth will behave. We have to be able to manipulate despite that uncertainty,” he continues. “For example, we’re able to put a placemat on a table in a particular position and avoid obstacles. We can do those types of tasks without knowing most of the parameters of the deformable object, like its stiffness or the friction values.”
“你永远不可能有一个完美的模型来描述绳子或布料的行为。尽管存在这种不确定性，但我们必须能够操作它们，“他继续说。“例如，我们可以在桌子上的特定位置放置一个垫子以避免障碍物。”我们可以在不知道变形物体的大部分参数(比如它的刚度或者摩擦值)的情况下完成这些任务，。

Earlier this year, Berenson received a National Science Foundation CAREER award to improve the ability of autonomous robots to handle soft, deformable objects. Berenson believes the challenges involved in picking up deformable objects such as cables, clothing, or even muscle tissue can be overcome by representing the object and task in terms of distance constraints and formulating control and planning methods based on this representation. Enabling robots in this way could allow medical robots to perform tedious tasks in surgery or make hospital beds, and in home service, allow robots to handle clothes and prepare food.
今年早些时候，Berenson获得了国家科学基金会CAREER奖，以奖励其在提升自主机器人处理柔软、可变形物体的能力方面所做的工作。Berenson认为，通过用距离约束来表示物体和任务，并在此基础上制定控制和规划方法，就可以克服在拾取电缆、衣服甚至肌肉组织等可变形物体时遇到的挑战。用这种方式制造机器人可以让医疗机器人在外科手术或医院病床上执行繁琐的任务，相应的在家庭服务中，机器人可以处理衣服和[准备食物](https://www.ri.cmu.edu/wp-content/uploads/2018/10/Oct2018_Michigan-ARM-Lab-Deformable-Manipulation.jpg)。

“We’re really excited about this work because we believe it will push the frontier on what robots can do with very limited information, which is essential for getting robots to work in people’s homes or in natural environments.”
“我们对这项工作非常兴奋，因为我们相信它将推动机器人在有限信息的情况下如何执行的进展，这对于让机器人在家庭或自然环境中工作至关重要。”

The ARM Lab is also working on algorithms for shape completion. This is particularly advantageous when you have a cluttered environment like a pile of clothing or other objects that need to be sorted.
ARM实验室也在研究形状补全的算法。当机器人处于一个杂乱的环境是，比如一堆衣服或其他需要分类的物品时，这种算法是特别有价值的。

“If you have a laser scanner and you scan something, you only see the front part of it. You have no idea what’s behind that or how far the object extends,” says Berenson. “We’ve been working on algorithms that allow us to basically fill in the part of the object that we don’t see.”
“如果你有一个激光扫描仪，你扫描的东西，你只能看到它的前面部分。你不知道后面是什么，也不知道物体延伸多远。“我们一直在研究算法，使我们能够基本上填满我们看不到的物体的部分。”

His team is taking advantage of a lot of the work already done by other researchers in deep neural networks for 3D reconstruction. Through machine learning, the algorithm has learned to look at a partial scan of an object and infer the parts of the shape it cannot see by looking at thousands of previously scanned objects. It turns out many household objects are very similar, so Berenson says they can get a pretty good prediction on household objects.
他的团队正在利用其他研究人员在深度神经网络中已经完成的许多工作来进行3D重建。通过机器学习，该算法学会了观察物体的部分扫描，并通过观察数千个先前扫描过的物体来推断出它看不到的形状部分。结果发现很多家居用品都非常相似，所以Berenson说，他们可以对家居用品做出很好的预测。

The research team is using some sophisticated robotic technology to test and verify their motion planning and manipulation algorithms. You will see a pair of KUKA LBR iiwa robot arms equipped with Robotiq 3-finger adaptive grippers manipulating everyday items of different shape, weight, and fragility. Watch the ARM Lab robots in action.
研究小组正在使用一些先进的机器人技术来测试和验证他们的运动规划和操作算法。你将会看到一对库卡LBR iiwa机器人手臂，装备了Robotiq 3指自适应夹爪，可以操纵不同形状、重量和易碎的日常物品。[观察ARM实验室机器人的工作。](http://bit.ly/2PByr25)

As robots begin to permeate our daily lives, disruption will come in many forms; not just technological. Social, ethical, legal and economic issues will raise concerns about privacy, liability, potential job loss, continued learning, and social conventions. One university is taking a closer look at the societal impact of robotics innovation.
随着机器人开始渗透到我们的日常生活中，变革将以多种形式出现;不仅仅体现在技术上。社会、伦理、法律和经济问题将引起人们对隐私、责任、潜在失业、持续学习和社会习俗的关注。一所大学正在更深入地研究机器人技术创新所带来的社会影响。

## Robot Ethics and Policy 机器人伦理与政策
At the heart of Corvallis, a city in central western Oregon about 50 miles from the Pacific Coast, we find a hidden gem. Part of the Willamette River Valley, the soil is very fertile here. Fertile ground for a rising star in the robotics field.
在距离太平洋海岸50英里的俄勒冈中西部城市科瓦利斯的中心，我们发现了一颗隐藏的宝石。威拉米特河谷的一部分，这里的土壤非常肥沃。这是机器人领域一颗冉冉升起的新星的沃土。

Oregon State University (OSU) is the city’s largest employer and home to the Collaborative Robotics and Intelligent Systems (CoRIS) Institute. Established in 2017 by OSU’s College of Engineering, CoRIS is mobilized to advance the design, development, and deployment of robots and intelligent systems able to interact seamlessly with people.
俄勒冈州立大学(OSU)是该市最大的雇主，也是协作机器人与智能系统研究所(CoRIS)的所在地。由俄勒冈州立大学工程学院于2017年成立的CoRIS公司致力于推进机器人和智能系统的设计、开发和部署，使其能够与人无缝互动。

“We’re moving away from the idea that robots are over there behind the fence and people are on this side,” says Kagan Tumer, Director of CoRIS and a professor in the School of Mechanical, Industrial and Manufacturing Engineering at Oregon State. “We’re interacting with robots everywhere, from factories, to work, to even in homes now we’re starting to see AI and robots bought by consumers. Understanding how people interact with a robot, whether it’s a simple vacuum cleaning robot or a home-care-level talking robot, there are a lot of questions about what it means to interact with a robot.”
“我们正在改变那种机器人在围栏里，而人在围栏外的固有认知，”CoRIS的主管、俄勒冈州立大学机械、工业和制造工程学院的教授Kagan Tumer说。“我们与机器人的交互无处不在，从工厂到办公室，甚至是家庭，现在我们开始看到消费者购买人工智能机器人。了解人们如何与机器人交互，无论是简单的清洁机器人还是家庭护理对话机器人，在人机交互方面有大量的问题需要研究。”

OSU researchers strive to address these questions through a strong collaborative research culture that is the hallmark of CoRIS. Multiple disciplines come together under one roof. There is also a unique focus on ethics and policy.
俄勒冈州立大学的研究人员努力通过强大的协作研究文化来解决这些问题，这是CoRIS的。多个学科在一个屋檐下走到一起。[在道德和政策方面也有特别的关注。](http://bit.ly/2EQ1k69)

“That’s something we take very seriously,” says Tumer. “Usually institutions like this have a research director and an academic director. We specifically have a policy and ethics director for the deployment side because we think it’s critical. We are one of the only places I know that have graduate-level robot ethics courses. We want our graduates to not only be technologically savvy, but also understand the implications of the robotics technology they put out into the world.”
“这是我们非常重视的事情，”Tumer说。通常像这样的机构都有一个研究主任和一个学术主任。我们特别为交付设置了一位政策和伦理主任，因为我们认为这很关键。我们是我所知道的仅有的几个有研究生水平的机器人伦理课程的机构之一。我们希望我们的毕业生不仅要精通技术，还能理解他们向世界引入的机器人技术的影响。

Oregon State’s CoRIS emphasizes the human element of robotics and AI. Researchers explore the ethical, political and legal implications of robotics to understand the scope and scale of the social and technological disruption, and its impact on the future of science, technology and society.
俄勒冈州立大学的CoRIS强调机器人和人工智能中人的因素。研究人员探索机器人技术的伦理、政治和法律意义，以了解社会和技术变革的范围和规模，以及对未来的科学、技术和社会带来的影响。

## Robotic Legged Locomotion 腿式移动机器人
Ethics and policy become more important as robots begin to share the same spaces as humans. Soon they will walk among us.
随着机器人开始与人类共享生活空间，伦理和政策变得越来越重要。不久他们就会来到我们身边。

Cassie, a bipedal robot developed in the labs at Oregon State, garners a lot of attention as it strolls around campus. The robot may resemble a pair of ostrich legs, but biomimicry was not the mission. Cassie’s developers simply wanted to create the most stable legged platform for varied terrain and unpredictable environments.
Cassie是俄勒冈州立大学实验室开发的两足机器人，它在校园漫步时吸引了很多关注。这个机器人看起来像两条鸵鸟腿，但仿生并不是它的目标。Cassie的开发人员只是想为各种地形和不可预知的环境创建最稳定的腿式平台。

The way Cassie would end up at OSU was no accident. In an effort to recruit top robotics talent, Tumer sought out Jonathan Hurst, who has a doctorate in robotics from Carnegie Mellon. He became the first Oregon State faculty devoted to robotics.
Cassie出现在俄勒冈州立大学并非偶然。为了招募顶尖的机器人专家，Tumer找到了Jonathan Hurst，他拥有CMU的机器人博士学位。他成为俄勒冈州第一个专门研究机器人技术的教员。

Hurst’s passion is legged locomotion, specifically passive dynamics of mechanical systems. He established the Dynamic Robotics Laboratory and his group designed and built ATRIAS, an early prototype to Cassie. ATRIAS gets its passive dynamics from series-elastic fiberglass springs, which act both as a suspension system and means of mechanical energy storage. The technology is based on the spring-mass model, a theory associated with the energy-efficient bouncing gait of animals. Imagine jumping on a pogo stick. Energy is stored in the spring when it’s compressed. When it expands, energy is released and you are thrust upwards.
Hurst酷爱是腿式移动机器人，特别是机械系统的被动动力学。他建立了Dynamic机器人实验室，他的团队设计并建造了[ATRIAS](http://bit.ly/1rooBjq)，这是Cassie的早期原型。ATRIAS的被动动力来源于串联弹性玻璃纤维弹簧，它既是悬架系统又是机械储能装置。这项技术基于弹簧-质量模型，这是一种与动物的节能跳跃步态相关的理论。想象一下在弹簧单高跷上跳，能量被压缩后储存在弹簧中。当它反弹时，能量被释放，你被向上推动。

“ATRIAS was a science experiment,” says Tumer. “It was never meant to be a robot in the real world. It was testing the idea of the models and the way that the passive dynamics of the robot works, and whether you can actually design a robot with very simple principles that would duplicate animal gait. Cassie is the outcome of that experiment.”
“ATRIAS是一个科学实验，”Tumer说。“它的目标并不是现实世界的机器人。它测试的是模型的概念和机器人被动动力学的工作方式，以及你是否可以用非常简单的原理设计一个机器人来模仿动物的步态。Cassie就是实验的[成果](https://www.ri.cmu.edu/wp-content/uploads/2018/10/Oct2018_Oregon-State-Cassie.jpg)。

With control over two more joints in each of its legs compared to ATRIAS, Cassie is able to maintain its balance even when standing still or crouching. Full range of motion in the hips enables Cassie to steer. It’s also half the weight of its predecessor but twice as powerful and more energy efficient. A sealed system allows it to operate in rain and snow. Many of Cassie’s components were custom-developed in OSU’s lab when the team was unable to find off-the-shelf components that were small enough or had the required performance.
与ATRIAS相比，Cassie的每条腿都多了两个关节，所以即使站着不动或蹲着也能保持平衡。臀部的全方位运动使Cassie能够转向。它的重量也只有前者的一半，但功率是前者的两倍，能效更高。密封系统使它能在雨雪中工作。许多Cassie的组件都是在俄勒冈州立大学的实验室[定制开发](http://bit.ly/2PrmnAm)的，当时该团队无法找到足够小的或具备所需性能的现成组件。

Oregon State spinoff Agility Robotics is marketing Cassie as a robust bipedal research platform for academic groups working on legged locomotion. The California Institute of Technology and University of Michigan are testing algorithms on Cassie to develop next-gen prosthetics and exoskeletons for persons with paraplegia. Beyond personal/assistive robotics, Tumer says the creators envision a career path for Cassie in package delivery and search and rescue applications.
俄勒冈州的分支机构Agility Robotics正将Cassie作为一个强大的双足研究平台推广给从事腿式移动机器人的学术团体。加州理工学院和密歇根大学正在Cassie上测试算法，为截瘫患者开发下一代假肢和外骨骼。Tumer说，除了个人/辅助机器人之外，创建者们也在构想Cassie在递送包裹和搜索救援方面的应用。

“We’re not that far now from having driverless vehicles,” he says. “If you can imagine a delivery truck that drives itself to your neighborhood, how do you handle that last 100 to 300 feet? That’s when legged robots pop out of the truck, deliver the package to your door, go back to the truck and drive to the next stop.”
“我们离拥有无人驾驶汽车不远了，”他说。“想象一下，一辆自动送货卡车自主开到你家附近，怎么处理这最后100到300英尺的距离? 这时，腿式机器人跳出卡车，把包裹送到门口，然后回到卡车上，开到下一站。“

Cassie’s creators are working on arm-like appendages to carry those packages and to right itself in case of a fall. Because Cassie will eventually need “eyes” to see your front door, vision and other sensors are on the agenda.
Cassie的创造者们正在研制一种类似手臂的附件，可以携带这些包裹，并在掉落时自行挑战。因为Cassie最终需要“眼睛”才能看到你家的前门，所以视觉和其他传感器也被提上了议程。

“If you look at the area around any house, from the curb to the sidewalk, to the slight slope of the driveway, to one or two steps in front of the house, it’s a hazard course for any type of wheeled robot,” says Tumer. “When you can pair a legged robot with a self-driving truck, you’re done. Being able to walk in environments designed for humans is going to be a big thing.”
Tumer说:“如果你观察任何房子的周围，从路边到人行道，到车道的小斜坡，再到屋前一两级台阶，这对任何类型的轮式机器人来说都是很大的考验。”“当你能把一个腿式机器人和一辆自动驾驶卡车组合在一起，这件事就搞定了。能在为人类设计的环境中行走将是一个里程碑。"

Investors like Andy Rubin’s Playground Global, Sony Innovation Fund, and Robotics Hub are banking on it. Albany, Oregon-based Agility Robotics raised $8 million in a Series A round in early 2018. In June, they opened a second location in Pittsburgh, where the startup plans to take advantage of the area’s strong talent pool in robotics. Meanwhile, research on future iterations of Cassie continues at Oregon State.
Andy Rubin的Playground Global、Sony Innovation Fund和Robotics Hub等投资者都对这一点满怀期望。总部位于俄勒冈州奥尔巴尼的Agility Robotics于2018年初获得A轮800万美元融资。6月份，他们在匹兹堡开设了第二家工厂，这家初创企业计划好好利用该地区强大的机器人人才库。与此同时，在俄勒冈州，对Cassie迭代的研究在持续进行。


## Multi-Robot Coordination 多机器人协作
Another significant research area for OSU is multi-robot coordination, Tumer’s main focus. He says many interesting real-world scenarios require multiple robots, or humans and robots, to work together. Search and rescue operations are one example.
OSU的另一个重要研究领域是多机器人协作，这是Tumer的主要研究方向。他说，许多有趣的现实场景需要多个机器人，或者人类和机器人一起工作。搜救行动就是一个例子。

“You might have unmanned aerial vehicles (UAV) looking for debris. You might have unmanned ground vehicles (UGV) moving around. You may have legged robots. You will have a lot of components doing a lot of different operations,” explains Tumer. “The critical aspect is how we determine what each one of those robots should be doing so the team does what you want it to do. Determining the objectives that you need to provide to all of these different robots is a key part of our research.”
“你可能有无人驾驶飞行器(UAV)在寻找残骸，你可能有无人地面车辆(UGV)在周围移动，你可能有腿式机器人，你会有很多不同机器人做不同的工作。“Tumer解释说，”关键在于我们如何决定这些机器人中的每一个应该如何分工，从而完成要求的任务。我们研究的一个关键部分就是如何为不同的机器人提供任务目标。“

Tumer says the different robots in a multi-robot team would need to have some level of awareness of the task they are trying to achieve, so they can determine how to best contribute to the team. His group is trying to impart that high level of coordination capability to robots.
Tumer说，多机器人团队中的不同机器人需要对他们要完成的任务有一定程度的认知，这样他们才能决定如何为团队做出最好的贡献。他的团队正试图将这种高水平的协调能力传授给机器人。

## Underwater Robotics 水下机器人
Tumer’s research in multi-robot coordination may also apply to underwater robots. Oregon State has a strong oceanography department and they collaborate with CoRIS, particularly with OSU professor Dr. Geoff Hollinger who focuses on underwater autonomy.
Tumer在多机器人协调方面的研究也可以应用于水下机器人。俄勒冈州立大学有一个强大的海洋学部门，他们与CoRIS合作，特别是与专注水下自主化的俄勒冈州立大学教授Geoff Hollinger博士合作。

“There’s a lot of underwater science that we do with robots,” says Tumer. “This is all about the health of the ocean, looking at how rivers bring the water and sediment, and how they propagate. There are a lot of research questions about how our environment is effected by everything we do, from runoff from rivers, to algae, to everything else. We have teams of intelligent gliders out there trying to collect information for our scientists.”
“我们用机器人做了很多水下科学研究，”Tumer说。“主要是研究海洋的健康，着眼于河流如何带来水和沉积物，以及它们如何繁殖。有很多研究是关于我们的环境是如何受到我们人类活动影响的研究的问题，比如从河流的径流，到藻类，到其他的一切。我们有一组智能滑翔机试图为我们的科学家们收集[相应信息](https://www.ri.cmu.edu/wp-content/uploads/2018/10/Oct2018_Oregon-State-Underwater-Glider.jpg)。

These “intelligent gliders” or autonomous underwater vehicles (AUV) look like small torpedoes, but have no engine. They glide with the water currents rather than being self-propelled. On-board sensors collect data on water salinity, temperature, nutrients and oxygen concentrations at various depths. The gliders can autonomously change their buoyancy to submerge up to 1,000 meter depths and then surface hours later to broadcast their data and location via satellite. They repeat this process every six hours or so, collecting data 24 hours a day for weeks at a time. Check out the video.
这些“智能滑翔机”或自主水下机器人(AUV)看起来像小型鱼雷，但没有引擎。它们是随着水流滑行而不是自我推进。船上的传感器收集不同深度的海水盐度、温度、营养和氧气浓度的数据。这些滑翔机可以自主地改变浮力，使其下沉到1000米深处，数小时后浮出水面，通过卫星向地面广播数据和位置。他们每隔6小时左右重复这个过程，连续数周每天24小时收集数据。[视频](http://bit.ly/2OViaoW)

Oregon State researchers working collaboratively from different disciplines in marine sciences and robotics are also equipping undersea gliders with bioacoustic sensors to identify different kinds of marine animals using their unique acoustical signatures. This helps scientists study the distribution of predators and prey, and their relationship to oceanic conditions.
俄勒冈州海洋科学和机器人技术的不同学科的研究人员合作，也为水下滑翔机配备了生物声学传感器，利用它们独特的声学特征识别不同种类的海洋动物。这有助于科学家研究捕食者和猎物的分布，以及它们与海洋环境的关系。 

Advanced control algorithms developed by Hollinger and the Robotic Decision Making Laboratory allow the gliders and other AUVs to more efficiently navigate strong currents and environmental disturbances, and respond to environmental cues. Enabling intelligent AUVs to gather information in environments outside the reach of human divers has long-term benefits for sustaining the fishing industry, protecting marine life, and understanding climate change.
Hollinger和Robotic Decision Making实验室开发的[先进控制算法](http://bit.ly/2qjDSnU)使滑翔机和其他水下机器人能够更有效地在强电流和环境干扰中航行，并对环境信号做出反应。让智能水下机器人在人类潜水员无法到达的环境中收集信息，对维持捕鱼业、保护海洋生物和理解气候变化具有长期益处。

As more robotic systems enter our waterways, streets and homes, researchers say we will need formal means of validation and testing to support deployment on a larger scale.
随着越来越多的机器人系统进入我们的水道、街道和家庭，研究人员表示，我们将需要规范的验证和测试手段来支持更大规模的部署。

## 机器人技术验证与测试 Robotics Validation and Testing
Carnegie Mellon’s Herbert thinks the not-so-exciting but perhaps most critical research area for robotics over the next 5 to 10 years will be integration, validation and testing. This is especially critical as human-robot interaction becomes a part of our daily lives. To illustrate his point, Herbert draws an analogy to the aircraft industry.
CMU的Herbert认为，在未来5到10年里，机器人技术最令人兴奋可能也是最关键的研究领域将是集成、验证和测试。随着人机交互成为我们日常生活的一部分，这一点尤为重要。为了说明他的观点，赫伯特用飞机工业做了一个类比。

“The flying public feels safe in a plane because we have 150 years of experience with a technology that has been validated and tested,” he says. “We don’t yet have those tools for AI and robotics. How do we do this for systems that learn over time, that adapt? Whose systems depend on the data they use to learn? How do we do this for a system that has complex interaction with people?
他表示:“在飞机上的公众感觉很安全，因为我们拥有150年的技术验证和测试经验。对于人工智能和机器人，我们还没有对应的工具。我们如何为那些随着时间的推移不断学习，不断适应的系统做这些呢?谁的系统依赖于他们用来学习的数据?对于一个与人有复杂互动的系统，我们如何做到这一点?

“For this relatively new field of robotics, we don’t yet have those engineering tools that allow us to guarantee performance, guarantee behavior of those systems,” says Hebert. “It’s what we need to be able to really use them in everyday applications. It’s this collection of best practices and formal tools that we need to get to a system you can actually trust.”
“对于这个相对较新的机器人领域，我们还没有那些工程工具来确保这些系统的性能和行为，”Hebert说。“这是我们在日常应用中真正使用它们时所必需的。我们需要的是这些最佳实践和正规工具的集合，才能建立一个你可以信任的系统。”

Trust will play a critical role in the acceptance of intelligent autonomous systems. Systems we can entrust to care for our loved ones and our most vulnerable populations, our children, our elderly; robots that will perhaps share our most intimate spaces; systems that will have access to our private data, details about our everyday activities, and privy to our conversations; robotic systems to which we will relinquish control. For that, they will need to earn our trust. Our bright future with robots depends on it. Researchers are helping us realize that future.
信任 将在人们可接受的智能自主系统中扮演关键角色。这些机器人系统获得我们授信照顾我们所爱的人，我们最脆弱的人群，我们的孩子，我们的父母；这些机器人也许会共享我们的私密空间；这些机器人系统能够访问我们的私人数据、我们日常活动的细节以及我们的对话；我们不得不放弃控制的机器人系统。为此，他们必须获得人类的信任。我们与机器人的美好未来有赖于此。科研人员正在帮助我们实现这个未来。

RIA Members featured in this article:
Carnegie Mellon University
University of Michigan

Originally published by RIA via www.robotics.org on 10/30/2018

# CMU RI More
CMU机器人学院规模庞大，涉及研究方向全面:

参考[CMU RI Research](https://www.ri.cmu.edu/research/) 的分类：

按应用领域 APPLICATION AREAS 分类： 
- Community, Education and Entertainment 社区，教育，娱乐
Big Data Visualization, CGI for Movies and Simulation, Community Empowerment, Intelligent Tutors, Technology Fluency & Education
大数据可视化，电影与仿真CGI，社区赋权，智能家教，技术流利度与教育

- Field Robotics 户外机器人
Aerial Robotics, Agriculture, Disaster Cleanup, Infrastructure, Inspection and Remediation, Space Exploration, Surveillance & Security, Urban Search and Rescue
无人机，农业，灾害清理，基础设施，巡检，空间探测，安防，城市搜救

- Manufacturing 制造业
Computer-Aided Fabrication Data-driven Analytics, Modular Manufacturing, Textiles Fabrication
计算机辅助制造数据驱动分析，模块化制造，纺织品制造

- Medical Robotics 医疗机器人
Augmented Reality for Medical Robotics, Biomedical Imaging, Rehabilitation Robotics, Robotic Surgery
增强现实医学机器人，生物医学成像，康复机器人，机器人手术

- Personal & Assistive Robotics 个人和辅助机器人
Companion Robotics, Exoskeletons, Personal Agents, Personal Mobile & Embedded Computing, Robots in the Home, Soft Robotics
配套机器人，外骨骼，个人代理，个人移动和嵌入式计算，家庭机器人，软机器人

- Transportation 运输
Self-Driving Cars & Vehicles, Smart Cities
自动驾驶汽车/车辆，智慧城市

学术研究按兴趣来即可，但要在工业界商业化，还是根据AI/DL技术的限制来选择：场景约束越多，越能落地。 室内比室外约束大，低速比高速，载物比载人安全

从教授们的研究方向来看：(细分方向)
- Field & Service Robotics 户外及服务机器人
Aerial Robotics, Industrial Robotics, Intelligent Transportation Systems, Manufacturing Robotics, Mining Robotics, Robotics for Scientific Discovery, Robotics in Agriculture and Forestry , Robotics in Construction, Robotics in Hazardous Application, Search and Rescue Robotics, Space Robots and Systems, Underwater Robotics
飞行机器人(无人机)，工业机器人，智能交通，制造业机器人，挖掘机器人，科学探索机器人，农林业机器人，建筑业机器人，危险应用机器人，搜救机器人，航空航天业机器人，水下机器人

- Graphics & Creative Tools 图形学
Animation, Augmented Reality, Computer-Aided Fabrication, First-Person Vision, Imaging, Rendering, Simulation, Textiles Manufacturing
动画，增强现实，计算机辅助制造，第一人称视觉，成像，渲染，仿真，纺织制造

- Human-Centered Robotics 以人为本的机器人
Biologically Inspired and Evolutionary Robotics, Domestic Robotics, Human Activity Forecasting, Human Robot Collaboration, Human-Robot Interaction, Humanoids, Medical Robotics and Computer-Integrated Surgery, Neurorobotics: From Vision to Action, Perceptual Robotics, Rehabilitation and Health Care Robotics, Roboethics: Social and Ethical Implications of Robotics, Robot Programming by Demonstration, Robots for Education, Safety for Physical Human-Robot Interaction, Social Robots
生物启发进化机器人，家用机器人，人类活动预测，人机协作，人机交互，人形机器人，医疗机器人和手术机器人，Neurorobotics:从视觉到行动，感知机器人，康复和护理机器人，Roboethics:社会和伦理的影响机器人，机器人示教，机器人教育，安全物理人机交互，社交机器人

- Manipulation & Interfaces 操控和接口
Behavior-based Systems, Contact Modeling and Manipulation, Cooperative Manipulators, Grasping, Haptics, Motion for Manipulation Tasks, Networked Robots, Robot Learning for Manipulation, World Modeling
基于行为的系统，接触建模和操作，协作操控，抓取，触觉，操作任务的运动，网络化机器人，机器人学习，世界模型

- Robot Structures 机器人结构
Kinematically Redundant Manipulators, Legged Robots, Micro/Nanorobots, Model Identification, Parallel Mechanism and Robots, Robot Hands, Robots with Flexible Elements, Soft Robotics, Wheeled Robots
机械手，腿式机器人，微型/纳米机器人，模型识别，并联机构和机器人，机器人手，柔性元件机器人，软机器人，轮式机器人

- Robotics Foundations 机器人基础
Active Perception, AI Reasoning for Articulated Systems, AI Reasoning for Multi-Robot Systems, AI Reasoning for Robotics, Business and Robotics, Computer Vision, Dynamics Force Control, Geometric Algorithms, Kinematics, Learning and Classification, Machine Learning Embedded in Systems, Mechanisms and Actuation, Motion Control, Motion Planning, Multi-Robot Planning & Coordination, Natural Language Processing, Planning & Scheduling, Reinforcement Learning, Robotic Systems Architectures and Programming
主动感知，链式系统AI推理，多机器人系统AI推理，机器人AI推理，机器人和商业，计算机视觉，动态力控，几何算法，运动学，学习和分类，机器学习嵌入系统，机制和驱动，运动控制，运动规划，多机器人的规划和协调，自然语言处理，规划和调度，强化学习，机器人系统架构和编程

- Sensing & Perception 传感器和感知
**3-D Vision and Recognition**, Facial Recognition, Force and Tactile Sensors, Internal Sensors, GPS, and Odometry, Multisensor Data Fusion, Sensing and Estimation, Simultaneous Localization and Mapping, Visual Servoing and Visual Tracking
三维视觉与识别，人脸识别，力与触觉传感器，内部传感器，GPS，里程计，多传感器数据融合，感知与估计，同步定位与制图，视觉伺服与视觉跟踪

## Courses
https://www.ri.cmu.edu/education/courses/
从 具体的 CMU RI 课程，以 16开头： All courses with a “16-” prefix are offered by the Robotics department. 

https://www.ri.cmu.edu/education/academic-programs/master-of-science-robotics/curriculum/
Students must pass four Core Courses, one course from each of the following four Core Areas: 
**Perception**: vision, image sensors, range data interpretation, tactile and force sensors, inertial guidance, and other sensors. Core courses in Perception are 16-720 Computer Vision, and 16-722 Sensing and Sensors.

**Cognition**: artificial intelligence for robotics, including knowledge representation, planning, and task scheduling, and learning. Core courses in Cognition are 15-780 Artificial Intelligence, and 10-601/10-701 Machine Learning.

**Action**: kinematics, dynamics, control, manipulation and locomotion. Core courses in Action are 16-741 Mechanics of Manipulation, and 16-711 Kinematics, Dynamic Systems and Control.

**Math Foundations**: signal processing, optimal estimation, differential geometry, and operations research. There is one core course in this area: 16-811 Math Fundamentals for Robotics.

---> UNDERGRADUATE COURSES
16-223  IDeATe: Introduction to Physical Computing
Physical computing refers to the design and construction of physical systems that use a mix of software and hardware to sense and respond to the surrounding world.
The course is organized around a series of practical hands-on exercises which introduce the fundamentals of circuits, embedded programming, sensor signal processing, simple mechanisms, actuation, and time-based behavior. The key objective is gaining an intuitive understanding of how information and energy move between the physical, electronic, and computational domains to create a desired behavior. 

16-264  Humanoids
This course surveys perception, cognition, and movement in humans, humanoid robots, and humanoid graphical characters. Application areas include more human-like robots, video game characters, and interactive movie characters.

16-311  Introduction to Robotics http://www.cs.cmu.edu/afs/cs.cmu.edu/academic/class/16311/www/current/
This course presents an overview of robotics in practice and research with topics including **vision, motion planning, mobile mechanisms, kinematics, inverse kinematics, and sensors.** 
In course projects, students construct robots which are driven by a microcontroller, with each project reinforcing the basic principles developed in lectures. Students nominally work in teams of three: an electrical engineer, a mechanical engineer, and a computer scientist. 

LEGO Mindstorms kits
Robotics, Vision, and Control, Peter Corke, Springer, 2011.

16-350  Planning Techniques for Robots http://www.cs.cmu.edu/~maxim/classes/robotplanning/
**Planning is one of the core components that enable robots to be autonomous. Robot planning is responsible for deciding in real-time what should the robot do next, how to do it, where should the robot move next and how to move there. ** This class does an in-depth study of popular planning techniques in robotics and examines their use in ground and aerial robots, humanoids, mobile manipulation platforms and multi-robot systems. 

16-384  Robot Kinematics and Dynamics
Foundations and principles of robotic kinematics. Topics include transformations, forward kinematics, inverse kinematics, differential kinematics (Jacobians), manipulability, and basic equations of motion. 

16-385  Computer Vision
This course provides a comprehensive introduction to computer vision. Major topics include image processing, detection and recognition, geometry-based and physics-based vision, sensing and perception, and video analysis. 
Computer Vision: Algorithms and Applications

16-450  Robotics Systems Engineering
Systems engineering examines methods of specifying, designing, analyzing and testing complex systems. In this course, principles and processes of systems engineering are introduced and applied to the development of robotic devices.

16-467  Human Robot Interaction
The field of human-robot interaction (HRI) is fast becoming a significant area of research in robotics. The basic objective is to create natural and effective interactions between people and robots. HRI is highly interdisciplinary, bringing together methodologies and techniques from robotics, artificial intelligence, human-computer interaction, psychology, education, and other fields. 

CV Master 课程： https://www.ri.cmu.edu/education/academic-programs/master-of-science-computer-vision/curriculum/

16-642  Manipulation, Estimation, and Control 操作，估算，控制

16-650  Systems Engineering & Management for Robotics
This course provides an overview of the current techniques that allow robots to locomote and interact with the world. The kinematics and dynamics of electromechanical systems will be covered with a particular focus on their application to robotic arms. Some basic principles of robot control will be discussed, ranging from independent- joint PID tracking to coupled computed torque approaches. The practice and theory of robotic mobility will be investigated through various mobile robot platforms, including wheeled and tracked vehicle and legged robots. 

16-623  Advanced Computer Vision Apps

16-662  Robot Autonomy  自主机器人
**Robot autonomy delves into the interplay between perception, manipulation, navigation, planning, and learning required to develop fully autonomous systems.**

16-665  Robot Mobility on Air, Land, & Sea

16-711  Kinematics, Dynamic Systems and Control 运动学，动态系统，控制

16-720  Computer Vision
16-722  Sensing & Sensors  传感器

16-745  Dynamic Optimization 最优控制
This course surveys the use of optimization (especially optimal control) to design behavior.

16-761  Introduction to Mobile Robots  http://www.frc.ri.cmu.edu/~alonzo/teaching/16-761/16-761.html
This course covers all aspects of mobile robot systems design and programming from both a theoretical and a practical perspective. The basic subsystems of control, localization, mapping, perception, and planning are presented.  

16-782  Planning and Decision-making in Robotics
Planning and Decision-making are critical components of autonomy in robotic systems. These components are responsible for making decisions that range from path planning and motion planning to coverage and task planning to taking actions that help robots understand the world around them better. 

16-785  Integrated intelligence in robotics: language, vision and planning
This course covers the topics on building cognitive intelligence for robotic systems. Cognitive capabilities constitute high-level, humanlike intelligence that exhibits reasoning or problem solving skills. Such capabilities as semantic perception, language understanding, and task planning can be built on top of low-level robot autonomy that enables autonomous control of physical platforms. 

16-811  Math Fundamentals for Robotics
This course covers selected topics in applied mathematics useful in robotics, taken from the following list: 1. Solution of Linear Equations. 2. Polynomial Interpolation and Approximation. 3. Solution of Nonlinear Equations. 4. Roots of Polynomials, Resultants. 5. Approximation by Orthogonal Functions (includes Fourier series). 6. Integration of Ordinary Differential Equations. 7. Optimization. 8. Calculus of Variations (with applications to Mechanics). 9. Probability and Stochastic Processes (Markov chains). 10. Computational Geometry. 11. Differential Geometry.

16-822   Geometry Based Methods in Computer Vision
The course focuses on the geometric aspects of computer vision: The geometry of image formation and its use for 3D reconstruction and calibration. 

16-823  Physics Based Methods in Vision

16-824  Learning-based Methods in Vision
We will be reading an eclectic mix of classic and recent papers on topics including: Theories of Perception, Mid-level Vision (Grouping, Segmentation, Poselets), Object and Scene Recognition, 3D Scene Understanding, Action Recognition, Contextual Reasoning, Image Parsing, Joint Language and Vision Models, etc. We will be covering a wide range of supervised, semi-supervised and unsupervised approaches for each of the topics above.

16-831  Statistical Techniques in Robotics
Data-driven learning techniques are now an essential part of building robotic systems designed to operate in the real world. These systems must learn to adapt to changes in the environment, learn from experience, and learn from demonstration. In particular we will cover three important sub-fields of Machine Learning applied to robotic systems: (1) We will cover **Online Learning**, which can be used to give robotic systems the ability to adapt to changing environmental conditions. (2) We will cover **Reinforcement Learning**, which takes into account the tradeoffs between exploration and exploitation to learn how to interact with the environment. We will also cover Deep Reinforcement Learning techniques in the context of real-world robotic systems. (3) We will cover **Apprenticeship Learning (Imitation Learning and Inverse Reinforcement Learning)** which is critical for teaching robotic systems to learn from expert behavior. Prerequisites: Linear Algebra, Multivariate Calculus, Probability theory.

16-833  Robot Localization & Mapping
Robot localization and mapping are fundamental capabilities for mobile robots operating in the real world. Even more challenging than these individual problems is their combination: simultaneous localization and mapping (SLAM).
http://frc.ri.cmu.edu/~kaess/teaching/16833/Spring2018

16-843  Manipulation Algorithms
This is an advanced graduate-level class on the theory and algorithms that enable robots to physically manipulate their world, on their own or in collaboration with people. The class will first focus on functional aspects of manipulation, such as synthesizing robust and stable grasps for dexterous hands and motion planning in these spaces, as well as learning for manipulation, such as how to predict stable grasps from demonstration and experience. 

16-848  Hands: Design and Control for Dexterous Manipulation
In this course, we will survey robotic hands and learn about the human hand with the goal of pushing the frontiers on hand design and control for dexterous manipulation. We will consider the necessary kinematics and dynamics for dexterity, what sensors are required to carry out dexterous interactions, the importance of reflexes and compliance, and the challenge of uncertainty. We will examine the human hand: its structure, sensing capabilities, human grasp choice and control strategies for inspiration and benchmarking. 

16-861  Mobile Robot Development
This course investigates robot mobility, energetics, sensing, computing, software, payload, interface, and operating environment. The context is robotic pursuit of the Moon. Scope incorporates mechanism, electronics, software, locomotion, navigation, communication, sensing, power and thermal considerations. 

16-865  Advanced Mobile Robot Development

16-868  Biomechanics and Motor Control
The course provides an introduction into the mechanics and control of legged locomotion with a focus on the human system. The main topics covered include fundamental concepts, muscle-skeleton mechanics, and neural control. 



# Stanford PAIR
Stanford大学是AI，机器人研究的[发源地](https://news.stanford.edu/2019/01/16/stanfords-robotics-legacy/) ： 从Shakey到Stanly，从STAIR到PR2，从Stanford Speech到ROS，ImageNet

Stanford [PAIR](http://pair.stanford.edu)是李飞飞, Silvio Savarese, Leonidas Guibas 三个教授领导的[Stanford Vision & Learning Lab](http://svl.stanford.edu/)下属的一个研究小组，”focuses on developing methods and mechanisms for generalizable robot perception and control.“

> We work on challenging open problems at the intersection of computer vision, machine learning, and robotics. We develop algorithms and systems that unify in reinforcement learning, control theoretic modeling, and 2D/3D visual scene understanding to teach robots to perceive and to interact with the physical world.

很多华人的身影：
- Jiajun Wu [吴佳俊](https://jiajunwu.com/) 
本科清华姚班，MIT博士，2020将加入SVL

- Yangyan Li [李扬彦](http://yangyan.li/)
中国科大博士, Stanford postdoctoral
His primary research interests fall in the field of Computer Graphics and Computer Vision, with an emphasis on 3D learning and vision. 3D perception for autonomous driving, including but not limited to point cloud/image based 3D reconstruction, recognition, segmentation, detection and pose estimation.

- Cewu Lu [卢策吾](http://mvig.sjtu.edu.cn/)
上海交大研究教授

> His research interests fall mainly in Computer Vision, deep learning, deep reinforcement learning and robotics vision.

- Hao Su [苏昊](http://cseweb.ucsd.edu/~haosu/)
PointNet的第一作者
本科毕业于北航高等理工学院，2017年获得Stanford Ph.D，在ucsd担任Assistant Professor at UC San Diego

> Professor Su is interested in fundamental problems in broad disciplines related to artificial intelligence, including machine learning, computer vision, computer graphics, robotics. 

他的博士论文 ： [Deep 3D Representation Learning](http://cseweb.ucsd.edu/~haosu/papers/thesis_finalversion.pdf)

- Charles Ruizhongtai Qi [祁芮中台](http://web.stanford.edu/~rqi/)
PointNet, PointNet++, Frustum PointNets的第一作者
浙江省2009高考理科第三名，2013清华本科EE，2018年Stanford CS Ph.D, Research Scientist at Waymo

> My research focuses on deep learning, computer vision and 3D. 

- Yuke Zhu [朱玉可](http://ai.stanford.edu/~yukez/)
浙大本科，2019年Stanford CS Ph.D，Assitant Professor in [UT-Austin](https://www.jiqizhixin.com/articles/2019-09-04-12)
博士论文 ： [Closing the Perception-Action Loop: Towards General-Purpose Robot Autonomy](http://ai.stanford.edu/~yukez/papers/yukezhu_phd_dissertation.pdf)

> My goal is to build intelligence for general-purpose robots that understand and interact with the real world. My research lies at the intersection of robotics, computer vision, and machine learning. I focus on developing methods and mechanisms of perception and control for general-purpose autonomy.


# UC Berkeley
两个实验室：
- [Berkeley Robot Learning Lab](http://rll.berkeley.edu/)
该实验室由[Pieter Abbeel](https://people.eecs.berkeley.edu/~pabbeel/)领导，Abbeel 2008年Stanford PHD毕业，是Andrew Y. Ng的学生.
主要研究方向 ： Deep Reinforcement Learning, Deep Imitation Learning, Deep Unsupervised Learning, Transfer Learning, Meta-Learning, and Learning to learn

- [Robotic AI & Learning Lab](http://rail.eecs.berkeley.edu/)
由Pieter Abbeel的博士生[Sergey Levine](https://people.eecs.berkeley.edu/~svlevine/)领导
> Our research focus is to enable machines to exhibit flexible and adaptable behavior, acquired autonomously through learning. To that end, we work on learning algorithms, robotics, and computer vision.

# Princeton Vision & Robotics
[该实验室](http://3dvision.princeton.edu/)的创始人是[肖建雄](http://www.jianxiongxiao.com/)，当前已投身自动驾驶创业，创建了[AutoX](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650730569&idx=3&sn=e591fe7f2c34016a8f641351af12f824&scene=0)
该实验室是学术界最先将深度学习应用到3D Vision领域，"参与发布目前最大的公共三维数据集（三维数据里的 ImageNet）ModelNet 和 ShapeNet ；创建了研究三维深度学习的基础网络框架 Marvin，为后来者做了铺垫；推出 3D 卷积网络 Deep Sliding Shapes，在 RGD-D 图像中研究三维物体的特征..."

> We study **Computer Vision and Robotics**, focusing on the computational principles underlying Artificial Intelligence. We are interested in building robots that automatically understand and interact with the physical worlds, both inferring the semantics and extracting 3D structure.

# CORL
正因为深度学习在AI领域取得的巨大进展，一些先行者认为需要将AI和机器人融合起来研究，发起全新的会议 ： Conference on Robot Learning/[CORL](https://www.robot-learning.org/)。会议第一次于2017年11月13日至15日在加州举行，会议论文 ： http://proceedings.mlr.press/v78/

The Conference on Robot Learning (CoRL) is a new annual international conference focusing on the intersection of robotics and machine learning. 
We invite papers offering new advances on any of the following topics:
- Imitation learning, bayesian/probabilistic learning, neural networks
- (Inverse) reinforcement learning, model-free learning, etc.
- Machine learning and control
- Bio-inspired learning and control
- State estimation, mapping, and computer vision
- Multimodal perception and sensor fusion
- Learning-based human robot interaction, natural language instruction processing
- Applications in manipulation, mobility, driving, flight, and other areas of robotics

# OpenAI
> OpenAI’s mission is to ensure that artificial general intelligence (AGI)—by which we mean highly autonomous systems that outperform humans at most economically valuable work—benefits all of humanity. We will attempt to directly build safe and beneficial AGI, but will also consider our mission fulfilled if our work aids others to achieve this outcome.

OpenAI Gym https://gym.openai.com/
A toolkit for developing and comparing reinforcement learning algorithms.

# 国内
- 清华大学人工智能研究院智能机器人研究中心 : 
2018年6月29日 - 6月28日,清华大学成立人工智能研究院 http://ai.tsinghua.edu.cn/
2019年5月30日 - 5月28日,清华大学人工智能研究院智能机器人研究中心成立
智能机器人研究中心旨在推进跨学科基础理论研究，密切结合人工智能、认知科学、生物材料、仿生学等领域的最新进展，与人工智能研究院其他中心通力合作，在机器人主动感知、认知学习、柔性操控等方向开展前膽性、基础性的理论与技术创新研究。

- 北京理工大学 智能机器人与系统高精尖创新中心 : http://baicirs.bit.edu.cn/index.htm
成立于2015年08月，围绕智能机器人与系统研究领域，综合运用分子仿生学、仿生机械学、多尺度感知与控制技术、多元人工智能技术等多门学科与前沿科学技术的交叉与融合

- 复旦大学 智能机器人研究院 : http://faet.fudan.edu.cn/13550/list.htm
成立于2017年1月，以智能计算、智能芯片、智能机器人及应用工程的交叉为突破点，以产业需求（医疗康复产业、智能制造产业、服务产业等）和重大任务（机器人国家重点研发计划、人工智能国家2030重大项目等）为牵引，研究智能机器人信息处理与控制、核心器部件、系统集成与应用等理论与技术。

- 浙江大学机器人研究院 http://rob.zju.edu.cn/index/science/detail/id/15.html

