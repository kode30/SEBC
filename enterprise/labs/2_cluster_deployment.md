
{
  "timestamp" : "2017-10-05T14:59:37.762Z",
  "clusters" : [ {
    "name" : "andreswagner",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "3213885440"
          }, {
            "name" : "hive_metastore_server_max_message_size",
            "value" : "321388544"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "3213885440"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "1775894528"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "298"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "cdh-srv1.c.safari-lab.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "cloudera"
        }, {
          "name" : "hive_metastore_database_user",
          "value" : "metastore"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-02c332011e48f05127820d00684115c6",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-23748e4f307f58bd03bee8384374909a",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7d9lbk85fdx1eogw9rkjg4nb1"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "86tszugosmiezvz22dnefpv5p"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "enableSecurity",
          "value" : "true"
        } ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-23748e4f307f58bd03bee8384374909a",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "db81itajoge9gl3m8ttepnyqs"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cebn3vs90u65c03qewhyzlax2"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "58j3f78sq7d9k6vjompo14k9x"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "cdh-srv1.c.safari-lab.internal"
        }, {
          "name" : "database_password",
          "value" : "cloudera"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-23748e4f307f58bd03bee8384374909a"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3lf05ovdkbhtm8dzcyj2pvtqq"
          }, {
            "name" : "secret_key",
            "value" : "RPJ8EcdqXnuHozPhhVvpwgzZenPHCd"
          } ]
        }
      }, {
        "name" : "hue-KT_RENEWER-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "KT_RENEWER",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "272dc15jnlzluhhxva7a6kbgb"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "cdh-srv1.c.safari-lab.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "cloudera"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "54knv0zl7szvbcnkw66bn48e4"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "12"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "8099"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "13424"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "8"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "X3vdFqyzEB6zI7kaHtQQCGjvmytSQj"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-23748e4f307f58bd03bee8384374909a",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bs9490qve8bzbp0re34ntf2yl"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-23748e4f307f58bd03bee8384374909a",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dcmb4vl9x3t38ioycsv2r4gn"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7piu8oc4l3gkrwjpzcas4b065"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "62mk6brtwnld65a6zkc2jxfx4"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-23748e4f307f58bd03bee8384374909a",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "50"
          }, {
            "name" : "role_jceks_password",
            "value" : "7i2nikyelnqpuh1pwde58b8j7"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_data_dir_perm",
            "value" : "700"
          }, {
            "name" : "dfs_datanode_http_port",
            "value" : "1006"
          }, {
            "name" : "dfs_datanode_port",
            "value" : "1004"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "3213885440"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "3213885440"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_encrypt_data_transfer_algorithm",
          "value" : "AES/CTR/NoPadding"
        }, {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "d1YIDdrXHnzoPB3G1Mh4ERGzVz01QF"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "B47VXA0EKsTs4k4jHOgkBXPRcQhDUV"
        }, {
          "name" : "hadoop_security_authentication",
          "value" : "kerberos"
        }, {
          "name" : "hadoop_security_authorization",
          "value" : "true"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "t10xzNoQWi8l5DD5SywvH9PNDQcKB7"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-23748e4f307f58bd03bee8384374909a",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ekrm862d1hm4wt3jq91sxrm8j"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "awolbsu93au1tbydjalsnt05o"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "41ocy5xsnuoyzt5f2fqaotdbg"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-23748e4f307f58bd03bee8384374909a",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "namenode_id",
            "value" : "52"
          }, {
            "name" : "role_jceks_password",
            "value" : "522rx3rc8jaq5zty4ul3ho8qy"
          } ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "SECONDARYNAMENODE",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "69kvjpfcii42v08bnrianmhds"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "impala",
      "type" : "IMPALA",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "IMPALAD",
          "items" : [ {
            "name" : "impalad_memory_limit",
            "value" : "268435456"
          }, {
            "name" : "scratch_dirs",
            "value" : "/impala/impalad"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "llama_am_ha_zk_auth_secret_key",
          "value" : "z0rHMCWFiJ4Krlg0nvc723fuaPCqMv"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        } ]
      },
      "roles" : [ {
        "name" : "impala-CATALOGSERVER-02c332011e48f05127820d00684115c6",
        "type" : "CATALOGSERVER",
        "hostRef" : {
          "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ej9hi3437pc74em3pczfjtm4f"
          } ]
        }
      }, {
        "name" : "impala-IMPALAD-23748e4f307f58bd03bee8384374909a",
        "type" : "IMPALAD",
        "hostRef" : {
          "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "brzeaj5uu794id8uja2lej67n"
          } ]
        }
      }, {
        "name" : "impala-IMPALAD-4898b54b4a7e251787de6bc7b74fbc2f",
        "type" : "IMPALAD",
        "hostRef" : {
          "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "55bxr9giby2lakepvt0gpvova"
          } ]
        }
      }, {
        "name" : "impala-IMPALAD-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "IMPALAD",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9h3aaws3kgj5umnlzoyn2a64x"
          } ]
        }
      }, {
        "name" : "impala-STATESTORE-02c332011e48f05127820d00684115c6",
        "type" : "STATESTORE",
        "hostRef" : {
          "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dnzwq7nxddczhxb4qf6xshu2h"
          } ]
        }
      } ],
      "displayName" : "Impala"
    }, {
      "name" : "sentry",
      "type" : "SENTRY",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SENTRY_SERVER",
          "items" : [ {
            "name" : "sentry_server_java_heapsize",
            "value" : "268435456"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "sentry_server_database_host",
          "value" : "cdh-srv1.c.safari-lab.internal"
        }, {
          "name" : "sentry_server_database_password",
          "value" : "cloudera"
        }, {
          "name" : "sentry_service_admin_group",
          "value" : "impala,hue,solr,kafka,andreswagner"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "sentry-GATEWAY-02c332011e48f05127820d00684115c6",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "sentry-SENTRY_SERVER-7f96486bfeba6a3a792fa62f69698ab8",
        "type" : "SENTRY_SERVER",
        "hostRef" : {
          "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6xgzxwoyj9qpyfxtxl83qtjgx"
          } ]
        }
      } ],
      "displayName" : "Sentry"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79",
    "ipAddress" : "10.128.0.5",
    "hostname" : "cdh-srv1.c.safari-lab.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "c0f1304d-648b-4a6a-9195-1c6b07f16068",
    "ipAddress" : "10.128.0.6",
    "hostname" : "cdh-srv2.c.safari-lab.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "f46d4c14-0c73-422d-9792-c22d62993c32",
    "ipAddress" : "10.128.0.8",
    "hostname" : "cdh-srv4.c.safari-lab.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "3e3526a6-66de-45da-a5a0-2815cc5e7f0e",
    "ipAddress" : "10.128.0.9",
    "hostname" : "cdh-srv5.c.safari-lab.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-02c332011e48f05127820d00684115c6",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "90ccc18008fe8d0556877ad620cac211aec9f88d3861decb697038622358c228",
    "pwSalt" : 1068830407223475430,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-02c332011e48f05127820d00684115c6",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "e1e30d34ecdd5afcd8b7221a52da8b8babedfaa56183ea5447ea37b966d9225f",
    "pwSalt" : -5572796429216235953,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-02c332011e48f05127820d00684115c6",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "e82ea5f2a5b85581cd99834c2296758cd43f0d35b3ce2be63c67e364e18a7823",
    "pwSalt" : 4597269425325997800,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-02c332011e48f05127820d00684115c6",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "6a0796edada6fd122d93f21540e0c71756049de63b509046147e721b2a5bc4d6",
    "pwSalt" : 989962495327396065,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-02c332011e48f05127820d00684115c6",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "f47cf6616d09e574ef76c291cc4badb396eee956c4940dfeb68129efe7e20c28",
    "pwSalt" : -8047952849634439091,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "72c99de1e9c2216478703e8f92fe9a3ce3d29e6f5311c20a36c363c171aaf768",
    "pwSalt" : -6580120299146796869,
    "pwLogin" : true
  }, {
    "name" : "andreswagner",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "a9901cff0ccf09daee7ec4452555d69ffaca4232b22f59737806ef1b95e8d557",
    "pwSalt" : 1577375679562977308,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "14022bbc67600393b0f55b7dd407d38e7e2cb2a597d41042f77595702108fa1f",
    "pwSalt" : 8007490387433022411,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.11.2",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170811-0014",
    "gitHash" : "3c3ea33a12076fb83a8f11c4452c52fac685d01b",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "cdh-srv1.c.safari-lab.internal"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "cloudera"
        }, {
          "name" : "firehose_database_user",
          "value" : "amon"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "cdh-srv1.c.safari-lab.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "cloudera"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-02c332011e48f05127820d00684115c6",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "3fxz8w7x7xg5qqbvaxunfln0n"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-02c332011e48f05127820d00684115c6",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "f153n6r7ge3vwappeb21j087k"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-02c332011e48f05127820d00684115c6",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "a9g7s8pd08hngo81aea7ty2rp"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-02c332011e48f05127820d00684115c6",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "mz4uyg8i1co8vpb9i88wngja"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-02c332011e48f05127820d00684115c6",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "6yedsx22mtivxfpbv95c0kihp"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-02c332011e48f05127820d00684115c6",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "5e1b9699-e260-44ba-85b9-7151e1360c79"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "1jf3clqd1e25jyuzag1213ovu"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "AD_USE_SIMPLE_AUTH",
      "value" : "false"
    }, {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/27/2012 9:20"
    }, {
      "name" : "KDC_ADMIN_PASSWORD",
      "value" : "BQIAAABEAAEAFUMuU0FGQVJJLUxBQi5JTlRFUk5BTAAMY2xvdWRlcmEtc2NtAAAAAVnVPKkBABcAEOiX/BhZDvIkN04fZL/YVbU="
    }, {
      "name" : "KDC_ADMIN_USER",
      "value" : "cloudera-scm@C.SAFARI-LAB.INTERNAL"
    }, {
      "name" : "KDC_HOST",
      "value" : "cdh-srv1.c.safari-lab.internal"
    }, {
      "name" : "KRB_ENC_TYPES",
      "value" : "arcfour-hmac"
    }, {
      "name" : "MAX_RENEW_LIFE",
      "value" : "604800"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "NOT_ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,http://archive.cloudera.com/kudu/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    }, {
      "name" : "SECURITY_REALM",
      "value" : "C.SAFARI-LAB.INTERNAL"
    } ]
  }
}
```
