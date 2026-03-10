
#整合后的关系
{
  "task": "RE",
  "language": "zh",
  "schema": {
    "关系定义总说明": "本关系体系覆盖交叉口知识图谱全模块（1.1-1.14空间骨架、2.1-2.7进口道设施、3.0车道级实体、安全隐患本体）的实体间关联，采用统一命名规范（小写+下划线），确保跨模块推理一致性",
    
    "一、空间层级关系（Spatial Hierarchy Relations）": "描述交叉口空间骨架的层级归属与拓扑连接，构建路口物理空间框架",
    
    "belongs_to": {
      "description": "空间归属关系，表明子实体隶属于父级空间实体（与contains互逆）",
      "domain": ["IntersectionApproach", "TrafficSign", "TrafficMarking", "OnStreetParking", "Median_NMVSeparationFacility", "SpeedBump", "ConvexMirror", "TrafficIsland", "ChannelizationGeometry", "UpstreamConstraint", "Lane", "LaneGroup", "LaneFunction", "LaneStorage", "LaneControl", "LaneSafety", "HazardEntity", "GeometricDesignHazard", "FacilityDefectHazard", "TrafficOrganizationHazard", "ManagementMaintenanceHazard", "EnvironmentalAdaptationHazard", "BehavioralRiskHazard"],
      "range": ["Intersection", "Approach", "Leg", "Road_Section", "Exit", "Quadrant", "Corner", "Median", "Edge"],
      "examples": [
        {"subject": "IntersectionApproach", "predicate": "belongs_to", "object": "Leg_North", "description": "进口道拓展段属于北进口路肢"},
        {"subject": "Lane", "predicate": "belongs_to", "object": "Approach", "description": "车道属于进口道"},
        {"subject": "HazardEntity", "predicate": "belongs_to", "object": "Intersection", "description": "隐患实体归属于交叉口"}
      ]
    },
    
    "contains": {
      "description": "空间包含关系，表明父级实体包含子级实体（与belongs_to互逆）",
      "domain": ["Intersection", "Approach", "Leg", "IntersectionApproach", "Road_Section"],
      "range": ["TrafficSign", "TrafficMarking", "OnStreetParking", "Median_NMVSeparationFacility", "SpeedBump", "ConvexMirror", "TrafficIsland", "Lane", "LaneGroup", "ChannelizationGeometry", "UpstreamConstraint", "Quadrant"],
      "examples": [
        {"subject": "Intersection", "predicate": "contains", "object": "Leg_North", "description": "交叉口包含北进口路肢"},
        {"subject": "IntersectionApproach", "predicate": "contains", "object": "TrafficIsland", "description": "进口道拓展段包含交通岛"}
      ]
    },
    
    "connected_to": {
      "description": "路网连接关系，描述路段与交叉口之间的拓扑连接",
      "domain": ["Road_Section"],
      "range": ["Intersection"],
      "examples": [
        {"subject": "Road_Section_People_Rd", "predicate": "connected_to", "object": "Intersection_001", "description": "人民路路段连接至交叉口"}
      ]
    },
    
    "adjacent_to": {
      "description": "横向邻接关系，描述同层级空间实体之间的空间邻接（用于变道、合流分析）",
      "domain": ["Lane", "Quadrant", "Corner"],
      "range": ["Lane", "Quadrant", "Corner"],
      "examples": [
        {"subject": "Lane_1", "predicate": "adjacent_to", "object": "Lane_2", "description": "1号车道与2号车道横向相邻"},
        {"subject": "Quadrant_NE", "predicate": "adjacent_to", "object": "Quadrant_SE", "description": "东北象限与东南象限相邻"}
      ]
    },
    
    "upstream_of": {
      "description": "纵向上下游关系，描述交通流方向上的上游关系（用于排队溢出溯源）",
      "domain": ["Lane", "Road_Section", "Intersection"],
      "range": ["Lane", "Road_Section", "Intersection"],
      "examples": [
        {"subject": "Lane_Entry", "predicate": "upstream_of", "object": "Lane_StopLine", "description": "进口段车道位于停止线车道的上游"},
        {"subject": "Intersection_A", "predicate": "upstream_of", "object": "Intersection_B", "description": "交叉口A位于交叉口B的上游"}
      ]
    },
    
    "downstream_of": {
      "description": "纵向上下游逆关系，与upstream_of互逆",
      "domain": ["Lane", "Road_Section", "Intersection"],
      "range": ["Lane", "Road_Section", "Intersection"],
      "examples": [
        {"subject": "Lane_Exit", "predicate": "downstream_of", "object": "Lane_Intersection", "description": "出口车道位于交叉口内部车道的下游"}
      ]
    },
    
    "located_at": {
      "description": "精确定位关系，描述功能实体或隐患实体在空间骨架上的具体挂载位置",
      "domain": ["TrafficSign", "TrafficMarking", "SpeedBump", "ConvexMirror", "OnStreetParking", "HazardEntity", "SignalLight", "IlluminationFacility", "MonitoringDevice"],
      "range": ["Lane", "Quadrant", "Corner", "Median", "Sidewalk", "StopLine"],
      "examples": [
        {"subject": "TrafficSign", "predicate": "located_at", "object": "Lane_1", "description": "交通标志位于1号车道上方"},
        {"subject": "HazardEntity", "predicate": "located_at", "object": "Corner_NE", "description": "隐患实体位于东北转角"}
      ]
    },
    
    "二、功能关联关系（Functional Association Relations）": "描述实体间的功能配合、控制、引导与分隔关系",
    
    "guides": {
      "description": "引导关系，标志/标线对车流/人流的指引作用",
      "domain": ["TrafficSign", "TrafficMarking", "ChannelizationGeometry"],
      "range": ["Lane", "Movement", "PedestrianCrossing", "NonMotorLane", "LaneFunction"],
      "examples": [
        {"subject": "TrafficSign", "predicate": "guides", "object": "Lane_1", "description": "交通标志指引1号车道"},
        {"subject": "TrafficMarking", "predicate": "guides", "object": "Left_Turn_Movement", "description": "左转箭头标线引导左转车流"},
        {"subject": "ChannelizationGeometry", "predicate": "guides", "object": "LaneFunction", "description": "渠化几何引导车道功能"}
      ]
    },
    
    "controls": {
      "description": "控制关系，信号/标志对通行行为的管制",
      "domain": ["TrafficSign", "SignalTimingPlan", "SignalPhase", "SignalLight"],
      "range": ["Lane", "LaneGroup", "Movement", "IntersectionApproach", "PedestrianCrossing"],
      "examples": [
        {"subject": "SignalPhase", "predicate": "controls", "object": "Lane", "description": "信号相位控制车道通行权"},
        {"subject": "SignalTimingPlan", "predicate": "controls", "object": "IntersectionApproach", "description": "信号配时方案控制进口道通行"}
      ]
    },
    
    "separates": {
      "description": "分隔关系，隔离设施对不同流向/类型交通的分隔",
      "domain": ["Median_NMVSeparationFacility", "TrafficIsland", "ChannelizationLine", "TrafficMarking"],
      "range": ["Lane", "Movement", "NonMotorFlow", "PedestrianFlow", "OppositeTraffic"],
      "examples": [
        {"subject": "Median_NMVSeparationFacility", "predicate": "separates", "object": "OppositeTraffic", "description": "中央隔离设施分隔对向交通流"},
        {"subject": "TrafficIsland", "predicate": "separates", "object": "Left_Turn_Movement", "description": "导流岛分隔左转车流与直行车流"}
      ]
    },
    
    "protects": {
      "description": "防护关系，安全设施对危险源或道路使用者的保护",
      "domain": ["Median_NMVSeparationFacility", "TrafficIsland", "SpeedBump", "ConvexMirror", "Guardrail", "CrashCushion"],
      "range": ["Pedestrian", "NonMotorVehicle", "Vehicle", "BlindZone", "ConflictPoint", "HazardousObject"],
      "examples": [
        {"subject": "Median_NMVSeparationFacility", "predicate": "protects", "object": "Pedestrian", "description": "隔离设施保护行人安全"},
        {"subject": "SpeedBump", "predicate": "protects", "object": "PedestrianCrossing", "description": "减速丘保护人行横道区域"},
        {"subject": "ConvexMirror", "predicate": "protects", "object": "BlindZone", "description": "凸面镜消除盲区保护通行安全"}
      ]
    },
    
    "restricts": {
      "description": "限制关系，设施对速度/行为的约束",
      "domain": ["SpeedBump", "TrafficSign", "SpeedLimitSign"],
      "range": ["VehicleSpeed", "VehicleType", "ParkingBehavior", "TrafficFlow"],
      "examples": [
        {"subject": "SpeedBump", "predicate": "restricts", "object": "VehicleSpeed", "description": "减速丘限制车速"},
        {"subject": "TrafficSign", "predicate": "restricts", "object": "ParkingBehavior", "description": "禁停标志限制停车行为"}
      ]
    },
    
    "marked_by": {
      "description": "标线标记关系，车道由标线界定和引导",
      "domain": ["Lane"],
      "range": ["TrafficMarking", "LaneLine", "StopLine", "Arrow", "EdgeLine", "ZebraCrossing"],
      "examples": [
        {"subject": "Lane", "predicate": "marked_by", "object": "LaneLine", "description": "车道由车道线标记"},
        {"subject": "Lane", "predicate": "marked_by", "object": "StopLine", "description": "车道终点由停止线标记"}
      ]
    },
    
    "illuminated_by": {
      "description": "照明关系，空间单元受照明设施覆盖",
      "domain": ["Lane", "PedestrianCrossing", "Intersection", "IntersectionApproach"],
      "range": ["StreetLight", "IlluminationProfile", "LightingFacility"],
      "examples": [
        {"subject": "Lane", "predicate": "illuminated_by", "object": "StreetLight", "description": "车道受路灯照明"},
        {"subject": "Intersection", "predicate": "illuminated_by", "object": "Overhead_Cantilever", "description": "交叉口受悬臂式路灯照明"}
      ]
    },
    
    "monitored_by": {
      "description": "监测关系，空间单元受监测设备覆盖",
      "domain": ["Lane", "Intersection", "IntersectionApproach", "PedestrianCrossing"],
      "range": ["Camera", "Detector", "TrafficSensor", "MeteorologySensor"],
      "examples": [
        {"subject": "Lane", "predicate": "monitored_by", "object": "Camera", "description": "车道受摄像头监测"},
        {"subject": "Lane", "predicate": "monitored_by", "object": "LoopDetector", "description": "车道受线圈检测器监测流量"}
      ]
    },
    
    "三、依赖约束关系（Dependency & Constraint Relations）": "描述实体间的依赖、触发与约束条件",
    
    "depends_on": {
      "description": "依赖关系，表明实体的存在或功能依赖于另一实体",
      "domain": ["TrafficSign", "SpeedBump", "ConvexMirror", "TrafficIsland", "SignalTimingPlan", "LaneWidth", "StorageLength"],
      "range": ["TrafficMarking", "LightingFacility", "TrafficSign", "SightDistance", "LaneConfiguration", "MaxQueueLength", "HeavyVehicleRatio"],
      "examples": [
        {"subject": "SpeedBump", "predicate": "depends_on", "object": "TrafficSign", "description": "减速丘依赖预告标志（无标志则存在法理隐患）"},
        {"subject": "ConvexMirror", "predicate": "depends_on", "object": "SightDistance", "description": "凸面镜设置依赖于视距不足的前提"},
        {"subject": "StorageLength", "predicate": "depends_on", "object": "MaxQueueLength", "description": "蓄车长度依赖于最大排队长度"}
      ]
    },
    
    "constrained_by": {
      "description": "约束关系，表明实体受其他实体条件限制",
      "domain": ["IntersectionApproach", "ChannelizationGeometry", "OnStreetParking", "Lane", "LaneFunction", "SignalTimingPlan"],
      "range": ["UpstreamConstraint", "TrafficState", "RoadSection", "BusStop", "AccessPoint", "SignalTiming", "GeometricDesign", "TrafficRegulation", "SafetyStandard"],
      "examples": [
        {"subject": "IntersectionApproach", "predicate": "constrained_by", "object": "UpstreamConstraint", "description": "进口道拓展段受上游设施距离约束"},
        {"subject": "ChannelizationGeometry", "predicate": "constrained_by", "object": "TrafficState", "description": "渠化几何受交通运行状态约束（如排队长度）"},
        {"subject": "Lane", "predicate": "constrained_by", "object": "SafetyStandard", "description": "车道宽度受安全标准约束"}
      ]
    },
    
    "triggers": {
      "description": "触发关系，某实体状态变化触发另一实体响应",
      "domain": ["TrafficState", "SpeedBump", "OnStreetParking", "EnvironmentalCondition", "HazardEntity"],
      "range": ["SignalTimingPlan", "TrafficSign", "EnforcementAction", "HazardAlert", "HazardEntity", "TrafficConflict"],
      "examples": [
        {"subject": "TrafficState", "predicate": "triggers", "object": "SignalTimingPlan", "description": "交通运行状态触发信号配时调整"},
        {"subject": "SpeedBump", "predicate": "triggers", "object": "HazardAlert", "description": "减速丘损坏触发隐患预警"},
        {"subject": "EnvironmentalCondition", "predicate": "triggers", "object": "HazardEntity", "description": "环境条件触发安全隐患"}
      ]
    },
    
    "calculated_from": {
      "description": "计算来源关系，属性值由其他实体属性计算得出",
      "domain": ["saturation_degree", "taper_ratio", "speed_diff_value", "green_utilization", "cycle_failure_rate", "SaturationDegree", "GreenUtilization"],
      "range": ["peak_hour_volume", "widening_offset", "taper_length_actual", "posted_speed_limit", "operating_speed_v85", "green_time", "cycle_length", "PeakHourVolume", "LaneWidth", "GreenTime"],
      "examples": [
        {"subject": "saturation_degree", "predicate": "calculated_from", "object": "peak_hour_volume", "description": "饱和度由高峰小时流量与设计通行能力计算"},
        {"subject": "SaturationDegree", "predicate": "calculated_from", "object": "PeakHourVolume", "description": "饱和度由高峰小时流量计算"},
        {"subject": "speed_diff_value", "predicate": "calculated_from", "object": "posted_speed_limit", "description": "速度差值由限速与运行车速计算"}
      ]
    },
    
    "determined_by": {
      "description": "决定关系，某属性由其他实体或条件决定",
      "domain": ["deceleration_len", "nose_offset_distance", "mounting_height", "signal_timing_plan", "LaneWidth", "StorageLength", "TurnRadius", "ControlPhase"],
      "range": ["max_queue_length", "design_speed", "vehicle_type", "traffic_state", "HeavyVehicleRatio", "MaxQueueLength", "DesignSpeed", "TrafficDemand"],
      "examples": [
        {"subject": "deceleration_len", "predicate": "determined_by", "object": "max_queue_length", "description": "减速储车段长度由最大排队长度决定"},
        {"subject": "LaneWidth", "predicate": "determined_by", "object": "HeavyVehicleRatio", "description": "车道宽度由大型车混入率决定"},
        {"subject": "TurnRadius", "predicate": "determined_by", "object": "DesignSpeed", "description": "转弯半径由设计速度决定"}
      ]
    },
    
    "四、冲突与隐患关系（Conflict & Hazard Relations）": "描述实体间的不协调、冲突及隐患关联",
    
    "conflicts_with": {
      "description": "冲突关系，表明两实体在功能或空间上存在矛盾",
      "domain": ["TrafficSign", "TrafficMarking", "OnStreetParking", "SpeedBump", "Median_NMVSeparationFacility", "Lane", "LaneFunction", "Movement", "TrafficFlow"],
      "range": ["TrafficSign", "TrafficMarking", "Lane", "SightDistance", "TrafficFlow", "PedestrianCrossing", "NonMotorLane", "AdjacentLane"],
      "examples": [
        {"subject": "TrafficSign", "predicate": "conflicts_with", "object": "TrafficMarking", "description": "标志与标线信息矛盾（如标志指示左转，标线为直行）"},
        {"subject": "OnStreetParking", "predicate": "conflicts_with", "object": "SightDistance", "description": "路侧停车与视距要求冲突（遮挡视线）"},
        {"subject": "LeftTurnLane", "predicate": "conflicts_with", "object": "OppositeStraightFlow", "description": "左转车道与对向直行车流冲突"}
      ]
    },
    
    "merges_with": {
      "description": "合流关系，交通流汇入其他交通流",
      "domain": ["Lane", "RightTurnLane", "Lane_Entry"],
      "range": ["Lane", "StraightLane", "MainFlow"],
      "examples": [
        {"subject": "RightTurnLane", "predicate": "merges_with", "object": "StraightLane", "description": "右转车道汇入直行车道"},
        {"subject": "Lane_Entry", "predicate": "merges_with", "object": "MainFlow", "description": "进口车道汇入主流"}
      ]
    },
    
    "diverges_from": {
      "description": "分流关系，交通流从其他交通流分出",
      "domain": ["Lane", "LeftTurnLane", "ExitLane"],
      "range": ["Lane", "StraightLane", "MainFlow"],
      "examples": [
        {"subject": "LeftTurnLane", "predicate": "diverges_from", "object": "StraightLane", "description": "左转车道从直行车道分流"},
        {"subject": "ExitLane", "predicate": "diverges_from", "object": "ThroughLane", "description": "出口车道从直行车道分流"}
      ]
    },
    
    "causes_hazard": {
      "description": "致害关系，某实体缺陷导致特定隐患",
      "domain": ["TrafficSign", "TrafficMarking", "OnStreetParking", "SpeedBump", "ConvexMirror", "Median_NMVSeparationFacility", "TrafficIsland", "SignalTimingPlan", "GeometricDesign"],
      "range": ["GeometricHazard", "FacilityDefect", "OrganizationHazard", "BehavioralRisk", "HazardEntity", "QueueSpillover", "HighDelay", "Congestion"],
      "examples": [
        {"subject": "TrafficSign", "predicate": "causes_hazard", "object": "FacilityDefect", "description": "标志缺失/遮挡导致设施缺陷类隐患"},
        {"subject": "TrafficMarking", "predicate": "causes_hazard", "object": "GeometricHazard", "description": "标线磨损导致几何线形指引失效隐患"},
        {"subject": "OnStreetParking", "predicate": "causes_hazard", "object": "OrganizationHazard", "description": "违法停车导致交通组织类隐患"},
        {"subject": "SpeedBump", "predicate": "causes_hazard", "object": "BehavioralRisk", "description": "减速丘设置不当导致驾驶行为风险（如急刹、绕行）"}
      ]
    },
    
    "exposes_to": {
      "description": "暴露关系，某实体使其他对象暴露于风险中",
      "domain": ["OnStreetParking", "SpeedBump", "TrafficIsland", "Median_NMVSeparationFacility", "HazardEntity"],
      "range": ["Pedestrian", "NonMotorVehicle", "Vehicle", "ConflictPoint", "Risk"],
      "examples": [
        {"subject": "OnStreetParking", "predicate": "exposes_to", "object": "Pedestrian", "description": "路侧停车使行人暴露于车流风险（压缩人行道）"},
        {"subject": "SpeedBump", "predicate": "exposes_to", "object": "NonMotorVehicle", "description": "减速丘设置不当使非机动车暴露于侧滑风险"}
      ]
    },
    
    "has_hazard": {
      "description": "隐患关系，空间单元存在特定安全隐患",
      "domain": ["Lane", "Intersection", "IntersectionApproach", "Road_Section"],
      "range": ["GeometricHazard", "OperationalHazard", "SafetyHazard", "ConflictPoint", "HazardEntity", "QueueSpillover", "HighFollowingRisk", "FunctionMismatch"],
      "examples": [
        {"subject": "Lane", "predicate": "has_hazard", "object": "QueueSpillover", "description": "车道存在排队溢出隐患"},
        {"subject": "Lane", "predicate": "has_hazard", "object": "HighFollowingRisk", "description": "车道存在高追尾风险"},
        {"subject": "Intersection", "predicate": "has_hazard", "object": "HazardEntity", "description": "交叉口存在安全隐患实体"}
      ]
    },
    
    "五、协同配合关系（Cooperation Relations）": "描述实体间的协同工作与信息互补",
    
    "cooperates_with": {
      "description": "协同关系，实体间功能互补配合",
      "domain": ["TrafficSign", "TrafficMarking", "SpeedBump", "ConvexMirror", "SignalTimingPlan", "SignalPhase"],
      "range": ["TrafficSign", "TrafficMarking", "LightingFacility", "SignalLight", "TrafficIsland", "ChannelizationGeometry"],
      "examples": [
        {"subject": "TrafficSign", "predicate": "cooperates_with", "object": "TrafficMarking", "description": "标志与标线协同指引（如限速标志配合限速标线）"},
        {"subject": "SpeedBump", "predicate": "cooperates_with", "object": "TrafficSign", "description": "减速丘与预告标志协同作用"},
        {"subject": "SignalTimingPlan", "predicate": "cooperates_with", "object": "TrafficIsland", "description": "信号配时与交通岛渠化协同优化"}
      ]
    },
    
    "complements": {
      "description": "补充关系，实体对另一实体的功能补充",
      "domain": ["ConvexMirror", "TrafficSign", "ChannelizationGeometry", "AuxiliaryFacility"],
      "range": ["SightDistance", "LaneConfiguration", "TrafficMarking", "SafetyFacility"],
      "examples": [
        {"subject": "ConvexMirror", "predicate": "complements", "object": "SightDistance", "description": "凸面镜补充视距不足"},
        {"subject": "TrafficSign", "predicate": "complements", "object": "TrafficMarking", "description": "标志补充标线无法表达的信息（如禁令）"},
        {"subject": "ChannelizationGeometry", "predicate": "complements", "object": "LaneConfiguration", "description": "渠化几何补充车道功能配置"}
      ]
    },
    
    "grouped_into": {
      "description": "分组关系，车道归属到车道组",
      "domain": ["Lane"],
      "range": ["LaneGroup"],
      "examples": [
        {"subject": "Lane_1", "predicate": "grouped_into", "object": "LaneGroup_N_Left", "description": "1号车道归入北进口左转车道组"},
        {"subject": "Lane_2", "predicate": "grouped_into", "object": "LaneGroup_N_Left", "description": "2号车道与1号车道同属一个左转车道组"}
      ]
    },
    
    "comprises": {
      "description": "组成关系，车道组由哪些车道组成（与grouped_into互逆）",
      "domain": ["LaneGroup"],
      "range": ["Lane"],
      "examples": [
        {"subject": "LaneGroup_N_Left", "predicate": "comprises", "object": "Lane_1", "description": "北进口左转车道组由1号车道组成"}
      ]
    },
    
    "六、运行与承载关系（Operation & Carrying Relations）": "描述交通流与空间单元的承载关系及运行状态",
    
    "carries": {
      "description": "承载关系，车道承载特定交通流",
      "domain": ["Lane", "IntersectionApproach", "Road_Section"],
      "range": ["TrafficFlow", "VehicleFlow", "NonMotorFlow", "PedestrianFlow", "PeakHourVolume"],
      "examples": [
        {"subject": "Lane", "predicate": "carries", "object": "MotorVehicleFlow", "description": "车道承载机动车流"},
        {"subject": "Lane", "predicate": "carries", "object": "PeakHourVolume_800", "description": "车道承载高峰小时流量800pcu/h"},
        {"subject": "BicycleLane", "predicate": "carries", "object": "NonMotorFlow", "description": "非机动车道承载非机动车流"}
      ]
    },
    
    "queues_at": {
      "description": "排队关系，车辆在车道特定位置排队",
      "domain": ["TrafficFlow", "Vehicle", "Queue"],
      "range": ["Lane", "StopLine", "LaneStorage", "IntersectionApproach"],
      "examples": [
        {"subject": "TrafficFlow", "predicate": "queues_at", "object": "Lane", "description": "交通流在车道排队"},
        {"subject": "Vehicle", "predicate": "queues_at", "object": "StopLine", "description": "车辆在停止线处排队"},
        {"subject": "Queue", "predicate": "queues_at", "object": "LaneStorage", "description": "排队发生在车道蓄车段"}
      ]
    },
    
    "overflows_to": {
      "description": "溢出关系，车道排队溢出至相邻空间",
      "domain": ["Queue", "MaxQueueLength", "LaneStorage"],
      "range": ["AdjacentLane", "UpstreamSection", "Intersection", "Lane"],
      "examples": [
        {"subject": "MaxQueueLength", "predicate": "overflows_to", "object": "AdjacentLane", "description": "最大排队长度溢出至相邻车道"},
        {"subject": "Queue", "predicate": "overflows_to", "object": "UpstreamSection", "description": "排队溢出至上游路段"},
        {"subject": "Lane_Storage", "predicate": "overflows_to", "object": "Intersection", "description": "蓄车不足导致排队溢出至交叉口内部"}
      ]
    },
    
    "experiences": {
      "description": "经历关系，车道经历特定运行状态",
      "domain": ["Lane", "IntersectionApproach", "Intersection"],
      "range": ["Delay", "Congestion", "Saturation", "LOS_Grade", "TrafficState"],
      "examples": [
        {"subject": "Lane", "predicate": "experiences", "object": "AvgDelay_45s", "description": "车道经历平均延误45秒"},
        {"subject": "Lane", "predicate": "experiences", "object": "Saturation_1.1", "description": "车道经历饱和度1.1的过饱和状态"},
        {"subject": "Lane", "predicate": "experiences", "object": "LOS_E", "description": "车道服务水平为E级（严重拥堵）"}
      ]
    },
    
    "七、时序与演化关系（Temporal Evolution Relations）": "描述实体在时间维度上的状态变化与演进",
    
    "evolves_to": {
      "description": "演进关系，实体状态随时间演变为另一状态",
      "domain": ["TrafficState", "TrafficMarking", "TrafficSign", "Median_NMVSeparationFacility", "LaneState", "TrafficCondition", "HazardEntity"],
      "range": ["TrafficState", "HazardState", "MaintenanceState", "CongestionState", "IncidentState"],
      "examples": [
        {"subject": "TrafficState", "predicate": "evolves_to", "object": "HazardState", "description": "交通运行状态恶化演变为隐患状态（如排队溢出）"},
        {"subject": "TrafficMarking", "predicate": "evolves_to", "object": "MaintenanceState", "description": "标线磨损演变为需维护状态"},
        {"subject": "HazardEntity", "predicate": "evolves_to", "object": "IncidentState", "description": "隐患演变为事故状态"}
      ]
    },
    
    "switches_to": {
      "description": "切换关系，可变车道功能切换",
      "domain": ["VariableLane", "TidalLane", "Lane"],
      "range": ["LaneFunction", "TimePeriod", "ControlStrategy", "Straight_Only", "Inbound_Direction"],
      "examples": [
        {"subject": "VariableLane", "predicate": "switches_to", "object": "Straight_Only", "description": "可变车道在特定时段转换为直行功能"},
        {"subject": "TidalLane", "predicate": "switches_to", "object": "Inbound_Direction", "description": "潮汐车道切换为 inbound 方向"}
      ]
    },
    
    "requires_maintenance": {
      "description": "维护需求关系，实体需要维护干预",
      "domain": ["TrafficMarking", "TrafficSign", "SpeedBump", "ConvexMirror", "Median_NMVSeparationFacility", "HazardEntity"],
      "range": ["MaintenanceAction", "InspectionPlan", "RectificationPlan"],
      "examples": [
        {"subject": "TrafficMarking", "predicate": "requires_maintenance", "object": "MaintenanceAction", "description": "磨损标线需要维护作业"},
        {"subject": "ConvexMirror", "predicate": "requires_maintenance", "object": "InspectionPlan", "description": "凸面镜需要定期巡检维护"},
        {"subject": "HazardEntity", "predicate": "requires_maintenance", "object": "RectificationPlan", "description": "隐患需要整改方案"}
      ]
    },
    
    "八、评估与优化关系（Evaluation & Optimization Relations）": "描述评估方法与优化措施的应用",
    
    "evaluated_by": {
      "description": "评估关系，实体接受特定评估",
      "domain": ["Lane", "LaneGroup", "Intersection", "IntersectionApproach", "HazardEntity"],
      "range": ["CapacityAnalysis", "LOSEvaluation", "SafetyAssessment", "DelayCalculation", "IRAPRiskAssessment"],
      "examples": [
        {"subject": "Lane", "predicate": "evaluated_by", "object": "CapacityAnalysis", "description": "车道接受通行能力分析"},
        {"subject": "Lane", "predicate": "evaluated_by", "object": "LOSEvaluation", "description": "车道接受服务水平评估"},
        {"subject": "Intersection", "predicate": "evaluated_by", "object": "IRAPRiskAssessment", "description": "交叉口接受IRAP风险评估"}
      ]
    },
    
    "optimized_by": {
      "description": "优化关系，实体通过特定措施优化",
      "domain": ["Lane", "LanePerformance", "LaneGroup", "Intersection", "SignalTimingPlan"],
      "range": ["SignalTimingAdjustment", "LaneReconfiguration", "ChannelizationImprovement", "RectificationPlan"],
      "examples": [
        {"subject": "Lane", "predicate": "optimized_by", "object": "SignalTimingAdjustment", "description": "车道通过信号配时调整优化"},
        {"subject": "Lane", "predicate": "optimized_by", "object": "LaneReconfiguration", "description": "车道通过重新配置功能优化"},
        {"subject": "HazardEntity", "predicate": "optimized_by", "object": "RectificationPlan", "description": "隐患通过整改方案优化"}
      ]
    },
    
    "九、安全隐患本体专用关系（Hazard Ontology Specific Relations）": "专门针对安全隐患本体的关系定义",
    
    "induces": {
      "description": "诱发关系，根源性隐患诱发衍生性隐患或危险行为",
      "domain": ["HazardEntity", "SafetyHazard", "GeometricHazard", "FacilityDefect"],
      "range": ["HazardEntity", "BehavioralRisk", "DangerousBehavior", "TrafficConflict"],
      "examples": [
        {"subject": "SignalVisibilityDefect", "predicate": "induces", "object": "RedLightRunningRisk", "description": "信号灯视认性不足诱发闯红灯行为风险"},
        {"subject": "YellowIntervalDefect", "predicate": "induces", "object": "DilemmaZoneRisk", "description": "黄灯时间不足诱发两难区风险"}
      ]
    },
    
    "exacerbates": {
      "description": "加剧关系，隐患加剧另一隐患的严重程度",
      "domain": ["HazardEntity"],
      "range": ["HazardEntity"],
      "examples": [
        {"subject": "LowFlowTimingDefect", "predicate": "exacerbates", "object": "RedLightRunningRisk", "description": "低流量配时不当加剧闯红灯风险"}
      ]
    },
    
    "is_prerequisite_of": {
      "description": "前提关系，隐患是另一隐患存在的前提条件",
      "domain": ["HazardEntity"],
      "range": ["HazardEntity"],
      "examples": [
        {"subject": "MotorNonMotorSeparationMissing", "predicate": "is_prerequisite_of", "object": "NonMotorVehicleWrongWayEntry", "description": "机非隔离缺失是非机动车逆行机动车道的前提"}
      ]
    },
    
    "manifested_as": {
      "description": "表现关系，设施或管理缺陷具体表现为特定行为风险",
      "domain": ["FacilityDefectHazard", "ManagementMaintenanceHazard", "TrafficOrganizationHazard"],
      "range": ["BehavioralRiskHazard"],
      "examples": [
        {"subject": "SignalTimingLogicDefect", "predicate": "manifested_as", "object": "RedLightRunningRisk", "description": "信号配时逻辑缺陷表现为闯红灯行为风险"}
      ]
    },
    
    "rooted_in": {
      "description": "根源关系，行为风险追溯至设施/几何/组织/管理缺陷根源",
      "domain": ["BehavioralRiskHazard"],
      "range": ["FacilityDefectHazard", "GeometricDesignHazard", "TrafficOrganizationHazard", "ManagementMaintenanceHazard"],
      "examples": [
        {"subject": "RedLightRunningRisk", "predicate": "rooted_in", "object": "SignalVisibilityDefect", "description": "闯红灯行为根源在信号灯视认性不足"},
        {"subject": "IllegalLaneChangeRisk", "predicate": "rooted_in", "object": "LaneFunctionMismatch", "description": "违规变道根源在车道功能不匹配"}
      ]
    },
    
    "generates": {
      "description": "生成关系，隐患产生特定类型的交通冲突",
      "domain": ["HazardEntity"],
      "range": ["TrafficConflict", "ConflictPoint"],
      "examples": [
        {"subject": "LeftTurnLaneMissing", "predicate": "generates", "object": "CrossingConflict", "description": "左转专用车道缺失生成交叉冲突"},
        {"subject": "RightTurnChannelizationDefect", "predicate": "generates", "object": "VehiclePedestrianConflict", "description": "右转渠化缺陷生成车辆-行人冲突"}
      ]
    },
    
    "has_potential_for": {
      "description": "潜在事故关系，隐患具有导致特定事故的潜在风险",
      "domain": ["HazardEntity"],
      "range": ["AccidentType", "AccidentRecord"],
      "examples": [
        {"subject": "SightTriangleObstruction", "predicate": "has_potential_for", "object": "RightAngleCollision", "description": "视距三角形遮挡隐患有直角碰撞事故潜力"},
        {"subject": "GuardrailEndDefect", "predicate": "has_potential_for", "object": "FrontalCollision", "description": "护栏端头缺陷有正面碰撞事故潜力"}
      ]
    },
    
    "violates": {
      "description": "违反关系，隐患违反特定标准规范",
      "domain": ["HazardEntity", "GeometricDesign", "FacilityInstallation"],
      "range": ["StandardClause", "DesignStandard", "SafetyStandard"],
      "examples": [
        {"subject": "IlluminationDeficiency", "predicate": "violates", "object": "CJJ_45_2015_4.1.2", "description": "照明亮度不足违反《城市道路照明设计标准》CJJ 45-2015第4.1.2条"},
        {"subject": "SightTriangleObstruction", "predicate": "violates", "object": "CJJ_152_2010_4.3.3", "description": "视距三角形遮挡违反CJJ 152-2010第4.3.3条"}
      ]
    },
    
    "complies_with": {
      "description": "符合关系，整改方案符合特定标准",
      "domain": ["RectificationPlan", "ImprovementMeasure"],
      "range": ["StandardClause", "DesignStandard"],
      "examples": [
        {"subject": "VegetationTrimmingPlan", "predicate": "complies_with", "object": "CJJ_152_2010_4.3.3", "description": "修剪绿化带整改方案符合CJJ 152-2010第4.3.3条"}
      ]
    },
    
    "assigned_to": {
      "description": "分配关系，隐患整改任务分配给特定责任主体",
      "domain": ["HazardEntity", "RectificationPlan"],
      "range": ["ManagementDepartment", "MaintenanceUnit", "TrafficPoliceDepartment"],
      "examples": [
        {"subject": "SignalFaultHazard", "predicate": "assigned_to", "object": "TrafficFacilityMaintenanceCenter", "description": "信号灯故障隐患分配给市交通设施维护中心"}
      ]
    },
    
    "depends_on_rectification_of": {
      "description": "整改依赖关系，隐患整改依赖于另一隐患的先行整改",
      "domain": ["HazardEntity"],
      "range": ["HazardEntity"],
      "examples": [
        {"subject": "PedestrianIslandSignalMissing", "predicate": "depends_on_rectification_of", "object": "PedestrianIslandSettingDefect", "description": "二次过街安全岛信号灯缺失整改依赖于安全岛设置整改"}
      ]
    },
    
    "mitigated_by": {
      "description": "缓解关系，隐患可被特定措施缓解",
      "domain": ["HazardEntity"],
      "range": ["SafetyFacility", "ManagementMeasure", "TrafficControlStrategy", "AuxiliaryFacility"],
      "examples": [
        {"subject": "SightDistanceDeficiency", "predicate": "mitigated_by", "object": "ConvexMirror", "description": "视距不足隐患可由凸面镜缓解"}
      ]
    },
    
    "interacts_with": {
      "description": "交互关系，隐患与另一隐患相互作用形成复合风险",
      "domain": ["HazardEntity"],
      "range": ["HazardEntity"],
      "examples": [
        {"subject": "LowIllumination", "predicate": "interacts_with", "object": "GlareInterference", "description": "低照度与眩光干扰交互形成复合视觉障碍"}
      ]
    },
    
    "synergizes_with": {
      "description": "协同关系，隐患与另一隐患协同产生叠加效应",
      "domain": ["HazardEntity"],
      "range": ["HazardEntity"],
      "examples": [
        {"subject": "WetRoadSurface", "predicate": "synergizes_with", "object": "SpeedingBehavior", "description": "雨天路滑与超速行为协同叠加增大事故风险"}
      ]
    },
    
    "supported_by": {
      "description": "数据支撑关系，隐患由特定检测数据支撑确认",
      "domain": ["HazardEntity"],
      "range": ["HighwayPavementProfile", "TrafficMeteorologyProfile", "TrafficState", "TrafficConflict", "AccidentRecord"],
      "examples": [
        {"subject": "SkidResistanceDeficiency", "predicate": "supported_by", "object": "PavementFrictionData", "description": "路面抗滑不足由路面摩擦系数检测数据支撑"},
        {"subject": "RightTurnConflictHazard", "predicate": "supported_by", "object": "RightTurnPedestrianConflictData", "description": "右转冲突隐患由右转-行人冲突热点数据支撑"}
      ]
    }
  }
}
