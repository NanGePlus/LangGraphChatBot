# 1、项目介绍
## 1.1、本次分享介绍    
**(第一期)[2025.2.26]LangGraph基础功能测试**                 
主要内容:LangGraph介绍，测试基础demo用例、记忆功能、工具集成、human-in-the-loop等功能                         

## 1.2 LangGraph介绍 
LangGraph 是由 LangChain 团队开发的一个开源框架，旨在帮助开发者构建基于大型语言模型（LLM）的复杂、有状态、多主体的应用           
它通过将工作流表示为图结构（graph），提供了更高的灵活性和控制能力，特别适合需要循环逻辑、状态管理以及多主体协作的场景            
比如智能代理（agent）和多代理工作流            
## 1.1 核心概念 
**图结构（Graph Structure）**              
LangGraph 将应用逻辑组织成一个有向图，其中：                    
节点（Nodes）:代表具体的操作或计算步骤，可以是调用语言模型、执行函数或与外部工具交互等                
边（Edges）:定义节点之间的连接和执行顺序，支持普通边（直接连接）和条件边（基于条件动态选择下一步）               
**状态管理（State Management）**              
LangGraph 的核心特点是自动维护和管理状态     
状态是一个贯穿整个图的共享数据结构，记录了应用运行过程中的上下文信息         
每个节点可以根据当前状态执行任务并更新状态，确保系统在多步骤或多主体交互中保持一致性               
**循环能力（Cyclical Workflows）**               
与传统的线性工作流（如 LangChain 的 LCEL）不同，LangGraph 支持循环逻辑          
这使得它非常适合需要反复推理、决策或与用户交互的代理应用         
例如，一个代理可以在循环中不断调用语言模型，直到达成目标                

## 1.2 主要特点
**灵活性:** 开发者可以精细控制工作流的逻辑和状态更新，适应复杂的业务需求            
**持久性:** 内置支持状态的保存和恢复，便于错误恢复和长时间运行的任务             
**多主体协作:** 允许多个代理协同工作，每个代理负责特定任务，通过图结构协调交互             
**工具集成:** 可以轻松集成外部工具（如搜索API）或自定义函数，增强代理能力           
**人性化交互:** 支持“人在回路”（human-in-the-loop）功能，让人类在关键步骤参与决策            
 
## 1.3 使用场景
LangGraph 特别适用于以下场景：             
**对话代理:** 构建能够记住上下文、动态调整策略的智能聊天机器人             
**多步骤任务:** 处理需要分解为多个阶段的复杂问题，如研究、写作或数据分析                
**多代理系统:** 协调多个代理分工合作，比如一个负责搜索信息、另一个负责总结内容的系统           

## 1.4 与 LangChain 的关系
LangGraph 是 LangChain 生态的一部分，但它是独立于 LangChain 的一个模块             
LangChain 更擅长处理简单的线性任务链（DAG），而 LangGraph 专注于更复杂的循环和多主体场景           
你可以单独使用 LangGraph，也可以结合 LangChain 的组件（如提示模板、工具接口）来增强功能                  


# 2、前期准备工作
## 2.1 开发环境搭建:anaconda、pycharm
anaconda:提供python虚拟环境，官网下载对应系统版本的安装包安装即可                                      
pycharm:提供集成开发环境，官网下载社区版本安装包安装即可                                               
**可参考如下视频:**                      
集成开发环境搭建Anaconda+PyCharm                                                          
https://www.bilibili.com/video/BV1q9HxeEEtT/?vd_source=30acb5331e4f5739ebbad50f7cc6b949                             
https://youtu.be/myVgyitFzrA          

## 2.2 大模型相关配置
(1)GPT大模型使用方案(第三方代理方式)                               
(2)非GPT大模型(阿里通义千问、讯飞星火、智谱等大模型)使用方案(OneAPI方式)                         
(3)本地开源大模型使用方案(Ollama方式)                                             
**可参考如下视频:**                                   
提供一种LLM集成解决方案，一份代码支持快速同时支持gpt大模型、国产大模型(通义千问、文心一言、百度千帆、讯飞星火等)、本地开源大模型(Ollama)                       
https://www.bilibili.com/video/BV12PCmYZEDt/?vd_source=30acb5331e4f5739ebbad50f7cc6b949                 
https://youtu.be/CgZsdK43tcY           
                

# 3、项目初始化
## 3.1 下载源码
GitHub或Gitee中下载工程文件到本地，下载地址如下：               
https://github.com/NanGePlus/LangGraphTest                             
https://gitee.com/NanGePlus/LangGraphTest                                 

## 3.2 构建项目
使用pycharm构建一个项目，为项目配置虚拟python环境             
项目名称：LangGraphTest                                
虚拟环境名称保持与项目名称一致                

## 3.3 将相关代码拷贝到项目工程中           
直接将下载的文件夹中的文件拷贝到新建的项目目录中                      

## 3.4 安装项目依赖          
命令行终端中直接运行如下命令安装依赖                  
pip install langgraph==0.2.74                  
pip install langchain-openai==0.3.6            


# 4、项目测试
分别在命令行终端中运行如下指令进行测试             
cd 01_BasicDemo        
python 01_demo.py            
python 02_demoWithMemory.py            
python 03_demoWithHumanInTheLoop.py            


 
