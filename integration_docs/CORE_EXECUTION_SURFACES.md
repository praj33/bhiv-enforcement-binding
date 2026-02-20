# CORE_EXECUTION_SURFACES.md

## Purpose

This document enumerates every location within BHIV Core where:

- Execution occurs
- Decisions are finalized
- Irreversible side effects occur

This is an explicit execution surface map for enforcement binding.

---

## Direct Execution Points

- mcp_bridge.py::handle_task
- mcp_bridge.py::query_knowledge_base
- mcp_bridge.py::handle_task_with_template
- core_api.py::execute_single_task
- core_api.py::execute_task_sequence
- cli_runner.py::run_task
- cli_runner.py::main
- start_demo.py::start_mcp_bridge
- start_demo.py::run_tests
- start_demo.py::demo_api_calls
- orchestration/core_orchestrator.py::execute_task
- orchestration/core_orchestrator.py::execute_sequence
- orchestration/core_orchestrator.py::_execute_with_agent
- agents/text_agent.py::process_text
- agents/text_agent.py::run
- agents/archive_agent.py::extract_pdf_text
- agents/archive_agent.py::process_pdf
- agents/archive_agent.py::run
- agents/audio_agent.py::transcribe_with_whisper
- agents/audio_agent.py::transcribe_with_wav2vec2
- agents/audio_agent.py::transcribe_with_speech_recognition
- agents/audio_agent.py::process_audio
- agents/audio_agent.py::run
- agents/image_agent.py::process_image
- agents/image_agent.py::run
- agents/knowledge_agent.py::query
- agents/knowledge_agent.py::process_task
- agents/agent_registry.py::find_agent
- reinforcement/agent_selector.py::select_agent
- reinforcement/model_selector.py::select_model
- utils/response_composer.py::compose_response
- utils/response_composer.py::_generate_with_template
- utils/qdrant_loader.py::test_search
- utils/qdrant_loader.py::initialize_pipeline
- core/events/core_events.py::accept_event
- core/events/core_events.py::get_event_status
- core/events/core_events.py::get_case_status
- core/events/webhooks.py::handle_escalation_result
- core/events/webhooks.py::handle_generic_callback
- core/events/webhooks.py::replay_failed_event
- core/events/webhooks.py::get_monitoring_events
- core/start_core_services.py::start_core_events_service
- core/start_core_services.py::start_webhooks_service
- integration/web_interface.py::upload_files
- integration/web_interface.py::process_voice
- integration/web_interface.py::download_nlo
- integration/web_interface.py::get_nlos
- integration/web_interface.py::test_tts
- integration/web_interface.py::get_voice_conversations
- integration/web_interface.py::get_task_status

---

## Action Finalization Points

- mcp_bridge.py::handle_task
- mcp_bridge.py::handle_task_with_template
- core_api.py::execute_single_task
- orchestration/core_orchestrator.py::execute_task
- orchestration/core_orchestrator.py::_execute_with_agent
- agents/text_agent.py::run
- agents/archive_agent.py::run
- agents/audio_agent.py::run
- agents/image_agent.py::run
- agents/knowledge_agent.py::query
- agents/agent_registry.py::find_agent
- reinforcement/agent_selector.py::select_agent
- reinforcement/model_selector.py::select_model
- utils/response_composer.py::compose_response
- core/events/core_events.py::accept_event
- core/events/webhooks.py::handle_escalation_result
- core/events/webhooks.py::handle_generic_callback
- integration/web_interface.py::upload_files
- integration/web_interface.py::process_voice

---

## Side Effect Surfaces

- mcp_bridge.py::log_task
- agents/agent_registry.py::load_agents
- agents/agent_registry.py::save_agents
- agents/agent_registry.py::register_agent
- agents/agent_memory_handler.py::add_memory
- agents/agent_memory_handler.py::save_memory
- agents/agent_memory_handler.py::load_memory
- agents/agent_memory_handler.py::cleanup_old_memories
- reinforcement/replay_buffer.py::add_run
- reinforcement/replay_buffer.py::save_buffer
- reinforcement/replay_buffer.py::load_buffer
- reinforcement/agent_selector.py::update_history
- reinforcement/model_selector.py::update_history
- reinforcement/rl_context.py::log_action
- reinforcement/rl_context.py::log_reward
- reinforcement/rl_context.py::log_task
- utils/mongo_logger.py::log_task_execution
- utils/mongo_logger.py::log_token_cost
- utils/mongo_logger.py::log_rl_action
- utils/mongo_logger.py::log_model_performance
- utils/mongo_logger.py::log_fallback_action
- utils/mongo_logger.py::get_cost_analytics
- utils/mongo_logger.py::get_fallback_analytics
- utils/mongo_logger.py::get_rl_performance_summary
- utils/task_logger.py::log_aim
- utils/task_logger.py::log_progress
- utils/task_logger.py::_write_log_entry
- utils/logger.py::log_to_mongo
- utils/logger.py::get_logger
- utils/qdrant_loader.py::create_collection
- utils/qdrant_loader.py::upload_documents
- core/karma_client.py::get_karma
- core/karma_client.py::update_karma
- core/karma_client.py::emit_karma_event
- core/events/webhooks.py::log_monitoring_event
- core/start_core_services.py::check_service_health

---

## Audit Assertion

This document represents the complete known execution surface of BHIV Core at time of audit.
Any new execution surface must be added here.