Flink Client的主要功能
	* Application Code运行
		* ExcutionEnvironment构建
		* 构建PackageProgram
		* 运行Application Code----PipelineExecution
		* 提取JobGraph
	* 任务管理
		* Submit Job
		* Cancel Job
		* Trigger SavePoint
		* JobStatus Track
	* 集群管理
		* 创建集群  ClusterDescriptor --- ClusterClient
		* 停止集群  ClusterClient
