# ROS Subscriber Latency

This repository discuss some reasons of the causes and affects for ROS subscribers' latency.

## Good Practice

This is a simple example of subscriber using lambda function.
```cpp
// Please disable the Nagle algorithm on your TCP sockets
ros::Subscriber sub = nh.subscriber<std_msgs::Bool>("topic_name", 1, 
    [this](const std_msgs::Bool::ConstPtr & msg)
    {
        // Do your thing here
    },
    ros::VoidConstPtr(),
    ros::TransportHints().tcpNoDelay()
)
```

## Reference

- https://answers.ros.org/question/360038/what-are-the-differences-between-the-different-transporthints/
